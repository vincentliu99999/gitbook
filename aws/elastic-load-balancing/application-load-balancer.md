# Application Load Balancer

[Application Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)

* 作為 OSI 第七層 application layer
* rule: priority, 1 個以上的 actions, 一個以上的 conditions
* target group: route request 至 registered targets
  * 1 個 target 可在多個 target group
  * 可設定 health checks，ALB 僅會將 request 送往 healthy target
  * routing 在不同 group 中是獨立的
  * 可設定 routing algorithm\(`Round robin` or `Least outstanding requests`\)

## Load Balancers <a id="application-load-balancers"></a>

* [Load Balancer Attributes](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/application-load-balancers.html#load-balancer-attributes)
* 預設 idel timeout 為 60 秒
* 可搭配 AWS WAF 透過 web ACL allow or block requests
* HTTPS listener 需有 SSL 憑證以及 [security policy](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/create-https-listener.html#describe-ssl-policies)

### Subnets for Your Load Balancer <a id="subnets-load-balancer"></a>

至少兩個 AZ，bitmask 至少 `/27`，至少要有 8 個可自由使用的 IP，load balancer 會使用這些 IP 跟 target 建立連線

### Load Balancer Security Groups <a id="load-balancer-security-groups"></a>

* rule 必須允許 listener 及 health check 的 port
* [建議的 SG Rules](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-update-security-groups.html#security-group-recommended-rules)

### Connection Idle Timeout <a id="connection-idle-timeout"></a>

* front-end connection: client &lt;---&gt; load balancer
  * idle timeout 預設 60 秒
* back-end connection: load balancer &lt;---&gt; target
  * EC2 建議啟用 HTTP keep-alive

### Load Balancer State <a id="load-balancer-state"></a>

1. provisioning: 設定中
2. active: 設定完成，可 route traffic
3. failed: 無法設定

### IP Address Type <a id="ip-address-type"></a>

Internet-facing load balancer 建立或 active 後可設定，internal load balancers 必須使用 IPv4 addresses

1. ipv4: IPv4 only
2. dualstack: IPv4 or IPv6

client 與 load balancer 溝通時，透過 IPv4 會解析出 A record，IPv6 則是 AAAA record。load balancer 與 target 溝通時，只會透過 IPv4

### Connection Idle Timeout <a id="connection-idle-timeout"></a>

* 在設定的時間內無任何資料傳送至 front-end connection 時會觸發 idle timeout，load balancer 將關閉連線
* 上傳檔案時，建議在 idle timeout 前至少送 1 byte 已延長 idle timeout
* 建議 application idle timeout 大於 load balancer idle timeout

## Listeners <a id="load-balancer-listeners"></a>

### Listener Configuration <a id="listener-configuration"></a>

支援 WebSockets, HTTP/2

* **Protocols**: HTTP, HTTPS
* **Ports**: 1-65535

### Listener Rules <a id="listener-rules"></a>

每個 listener 都有 default rule，rule 由 priority、actions、conditions 組成

* Default Rules 不能有 conditions，沒有符合的 rule 就會執行
* Rule Priority，由低到高
* [Rule Actions](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html#rule-action-types) type, order, information
  * fixed-response
  * forward: 需先建立 target group
  * redirect
* [Rule Conditions](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html#rule-condition-types) type, configuration

## Target Groups <a id="load-balancer-target-groups"></a>

* route request 到註冊的 target。預設會有 health check 可自行 override
* [attribute](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html#target-group-attributes)

### Target Type <a id="target-type"></a>

* instance
* ip
* lambda

### Registered Targets <a id="registered-targets"></a>

* target 可存在 1 或多個 target group
* 需求增加時可註冊額外 target，需求減少或 resource 需要維護時可取消註冊
* target 註冊 instance Id 時，可利用 [auto scaling group](https://docs.aws.amazon.com/autoscaling/ec2/userguide/attach-load-balancer-asg.html)

### Routing Algorithm <a id="modify-routing-algorithm"></a>

* round robin: request, target 相似
* least outstanding

### Deregistration Delay <a id="deregistration-delay"></a>

* 停止發送 request 到 deregistering target，預設 300 秒等待 in-flight requests 完成
* 如果沒有 in-flight requests 或 active 連線 deregistration 流程會馬上結束，但 target 的壯代會維持在 draining 直到結束

## Monitor Your Application Load Balancers <a id="load-balancer-monitoring"></a>

* CloudWatch metrics
* Access logs
* Request tracing
* CloudTrail logs

### CloudWatch Metrics

* name space:  `AWS/ApplicationELB` for loadbalancer and target

