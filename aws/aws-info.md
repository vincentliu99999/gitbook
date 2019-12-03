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

