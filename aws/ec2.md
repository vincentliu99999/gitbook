# EC2

## Elastic Load Balancing

[Health Check](https://docs.aws.amazon.com/zh_tw/elasticloadbalancing/latest/classic/elb-healthchecks.html)

調整 Health Check 降低 AllowTraffic

條整 Deregistration Delay 降低 BlockTraffic

## Reference

* [AWS 替 CodeDeploy 加入 Load balancer 的功能](https://shazi.info/aws-%E6%9B%BF-codedeploy-%E5%8A%A0%E5%85%A5-load-balancer-%E7%9A%84%E5%8A%9F%E8%83%BD/) 降低 AllowTraffic
* [BlockTraffic/AllowTraffic durations](https://forums.aws.amazon.com/thread.jspa?threadID=254752)
* [AWS CodeDeployの速度改善\(ALB\)](https://qiita.com/tomozo6/items/1c436f594e2cce486153) 降低 BlockTraffic, AllowTraffic
* [取消註冊的延遲](https://docs.aws.amazon.com/zh_tw/elasticloadbalancing/latest/application/load-balancer-target-groups.html#deregistration-delay)
* [Environment Configuration Options In Elastic Beanstalk](https://cloudaffaire.com/environment-configuration-options-in-elastic-beanstalk/)

