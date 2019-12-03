# AWS CLI

## [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/index.html)

### Cloudwatch

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

