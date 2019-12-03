# CloudWatch

## Problem

### DataAlreadyAcceptedException

```text
2019-08-15 05:09:54,795 - cwlogs.push.publisher - WARNING - 4399 - Thread-5 - Caught exception: An error occurred (DataAlreadyAcceptedException) when calling the PutLogEvents operation: The given batch of log events has already been accepted. The next batch can be sent with sequenceToken: 49594357288396454084208559308983606612690881501775034066
```

Solution from stackoverflow - [logs from only some files showing up aws cloudwatch](%20https://stackoverflow.com/questions/39151342/logs-from-only-some-files-showing-up-aws-cloudwatch)

It's possible your agent state file is corrupted because you kept making changes to the configuration. There are two ways to fix this:

* **Option 1:** Use a new name for your configuration block header.
  * That is, change `[/var/log/cron]` to `[/something/else]`.
* **Option 2:** Delete the agent state file after stopping the service.

  ```text
  sudo service awslogs stop && sudo rm /var/lib/awslogs/agent-state && sudo service awslogs start

  sudo service awslogs stop
  sudo rm /var/lib/awslogs/agent-state
  sudo service awslogs start
  ```

Please note that Option 2 may initially cause duplicate logs to be pushed to CloudWatch as a new state file is created.

### InvalidSequenceTokenException

```text
2019-08-15 03:20:46,505 - cwlogs.push.publisher - WARNING - 2580 - Thread-7 - Caught exception: An error occurred (InvalidSequenceTokenException) when calling the PutLogEvents operation: The given sequenceToken is invalid. The next expected sequenceToken is: 49598360192768937424286658454601820169626161987109027154
```

### ResourceNotFoundException

```text
2019-08-15 03:25:27,257 - cwlogs.push.publisher - WARNING - 2986 - Thread-7 - Caught exception: An error occurred (ResourceNotFoundException) when calling the PutLogEvents operation: The specified log group does not exist.
```

## Reference

* [Agent Reference](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AgentReference.html)

