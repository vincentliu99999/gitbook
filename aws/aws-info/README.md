# AWS Info

## Proxy Setting

```text
sudo vim /etc/yum.conf
```

## Config

### Cloudwatch Config

```text
# region setting
sudo less /var/awslogs/etc/aws.conf
# log settings
sudo less /var/awslogs/etc/awslogs.conf
sudo less /var/awslogs/etc/proxy.conf
```

## Log

### Cloudwatch Log

```text
# view agent setup log
sudo less /var/log/awslogs-agent-setup.log

# view agent logs
sudo less /var/log/awslogs.log
```

## SDK

* Python: [Boto 3](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html)
* [Javascript](https://docs.aws.amazon.com/sdk-for-javascript/?id=docs_gateway)
* [Java](https://docs.aws.amazon.com/sdk-for-java/?id=docs_gateway)



