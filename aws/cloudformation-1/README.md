# CloudFormation

* Stack: 一群  AWS Resources
  * Nested Stacks: 利用 `AWS::CloudFormation::Stack` 建立部分的 stack，讓其他 template 參照。Nested Stacks 可以包含 Nested Stacks
* StackSets 跨 account, region

{% hint style="info" %}
AWS::EC2::Image::Id 無 drop down list，CloudFormation 僅會驗證 image Id 有效

參數名稱會依字母順序排列，可用 `AWS::CloudFormation::Interface` [指定排列順序](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudformation-interface.html)
{% endhint %}

機敏資訊可使用 System Manager 或是 Secrets Manager

## 參考資料

* [AWS CloudFormation Limits](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cloudformation-limits.html)
* [Template Snippets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/CHAP_TemplateQuickRef.html)

## Issue

* Encountered non numeric value for property ToPort
* Exactly one of CidrIp, CidrIpv6, DestinationSecurityGroupId, and DestinationPrefixListId must be specified and not empty

