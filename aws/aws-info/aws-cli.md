# AWS CLI

## [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/index.html)

```bash
aws xxx --debug
aws xxx --profile <profile-name>
aws xxx --region <region-name>
```

### [Cloudwatch](https://docs.aws.amazon.com/cli/latest/reference/cloudwatch/index.html)

[Schedule Expressions for Rules](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/ScheduledEvents.html)

```bash
aws events list-rules

# EC2 營業時間：週一至週五 9:00~20:00
aws events put-rule --name "start-EC2-freebird" --schedule-expression "cron(0 1 ? * MON-FRI *)"
aws events put-rule --name "stop-EC2-freebird" --schedule-expression "cron(0 12 ? * MON-FRI *)"

# EC2 營業時間：週一至週六 9:00~20:00
aws events put-rule --name "start-EC2-freebird" --schedule-expression "cron(0 1 ? * MON-SAT *)"
aws events put-rule --name "stop-EC2-freebird" --schedule-expression "cron(0 12 ? * MON-SAT *)"
```

### [CloudFormation](https://docs.aws.amazon.com/cli/latest/reference/cloudformation/index.html)

```bash
# 列出您帳戶中的所有堆疊。可用於檢視堆疊集及其目前狀態
aws cloudformation list-stacks

# 列出建立堆疊時建立的所有 AWS 資源名稱和識別符
aws cloudformation list-stack-resources --stack-name Dns-resolver

# 針對堆疊產生的所有操作和事件
aws cloudformation describe-stack-events --stack-name Dns-resolver
```

### [DynamoDB](https://docs.aws.amazon.com/cli/latest/reference/dynamodb/index.html)

```bash
aws dynamodb list-tables
```

### [SES](https://docs.aws.amazon.com/cli/latest/reference/ses/index.html)

```text
aws ses list-identities --region us-west-2
```

