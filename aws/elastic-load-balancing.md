---
description: 分配 target 流量
---

# Elastic Load Balancing

* [比較 LB](https://aws.amazon.com/tw/elasticloadbalancing/features/#compare) \| [Pricing](https://aws.amazon.com/tw/elasticloadbalancing/pricing/)\(hr or LCU\) \| [Demo](https://exampleloadbalancer.com/)
* listener: 透過 port, protocol 檢查 client 連線 request 的流程
* 類別
  * Application Load Balancers, by `target groups`, 預設 multi AZ\(建議選項\)
  * Network Load Balancers, by `target groups`
  * Classic Load Balancers, by `instances`
* [CLB Migration](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/migrate-to-application-load-balancer.html)

## How Elastic Load Balancing Works <a id="how-elastic-load-balancing-works"></a>

### Request Routing

load balancer domain name 由 Amazon DNS servers 控制\(`amazonaws.com`\)，DNS servers 會回傳 1 或多個 IP 位址，TTL 預設 60 秒

client 可決定要用哪組 IP，load balancer 會選擇 healthy registered target 將 request 送到他的 private IP

#### Routing Algorithm <a id="routing-algorithm"></a>

ALB

1. 依據 priority 決定要用哪個 rule
2. 由 rule action 中的 target group 選擇一個 target，使用 target group 所設定的 routing algorithm。預設 round robin

#### HTTP Connections <a id="http-connections"></a>

ALB

* 使用 connection multiplexing，client 的 request connection 都會 routed 到固定一組 target。如果不需要，可以在 HTTP response header 設定 `Connection: close` 來取消 HTTP `keep-alives`
* front-end connections: HTTP/0.9, HTTP/1.0, HTTP/1.1, and HTTP/2.
* idle timeout 預設 60 秒，連線 idle 時間超過時，會被阻斷並收到 error response

#### HTTP Headers <a id="http-headers"></a>

* **X-Forwarded-For**, **X-Forwarded-Proto**, and **X-Forwarded-Port**
* \*\*\*\*[限制](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html#http-header-limits)

### Load Balancer Scheme <a id="load-balancer-scheme"></a>

1. internal public 有 IP addresses
2. internet-facing 僅有 private IP addresses，可存取 VPC 的 client 才能使用

## Security in Elastic Load Balancing <a id="security"></a>

## [Application Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html) <a id="introduction"></a>

* 作為 OSI 第七層 application layer
* rule: priority, 1 個以上的 actions, 一個以上的 conditions
* target group: route request 至 registered targets
  * 1 個 target 可在多個 target group
  * 可設定 health checks，ALB 僅會將 request 送往 healthy target
  * routing 在不同 group 中是獨立的
  * 可設定 routing algorithm\(`Round robin` or `Least outstanding requests`\)

{% hint style="info" %}
每個 listener 都必須定義一個預設的 rule
{% endhint %}

## Load Balancers <a id="application-load-balancers"></a>

### Subnets for Your Load Balancer <a id="subnets-load-balancer"></a>

至少兩個 AZ，bitmask 至少 `/27`，至少要有 8 個可自由使用的 IP，load balancer 會使用這些 IP 跟 target 建立連線

### Load Balancer Security Groups <a id="load-balancer-security-groups"></a>

rule 必須允許 listener 及 health check

[建議的 SG Rules](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-update-security-groups.html#security-group-recommended-rules)

### Connection Idle Timeout <a id="connection-idle-timeout"></a>

* front-end connection: client &lt;---&gt; load balancer
  * idle timeout 預設 60 秒
* back-end connection: load balancer &lt;---&gt; target
  * EC2 建議啟用 HTTP keep-alive

