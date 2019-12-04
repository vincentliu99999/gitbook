# CloudFormation

## [What is AWS CloudFormation?](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html)

### **AWS CloudFormation Concepts**

* 使用 template 描述運用的 AWS 資源及屬性
* 簡化 Infrastructure 管理，免個別設定，省時省力省複雜度
* 快速複製 Infrastructure 到不同 AZ
* 簡易控制及變更，修改 template 即可

### **How Does AWS CloudFormation Work**

* 僅能使用你有權限動用的資源
* template 可為 JSON 或 YAML 格式，包含資源及設定
* 存在 local 或 S3
* 設定可由參數做設定
* stack: template 資源建立完成，stack 建立失敗時 CloudFormation 將取消變更並把以建立的資源刪除
  * 變更: 建立 change set 修改 template、預覽變更、執行變更
    * 可能會導致中斷，詳洽 [AWS CloudFormation Stack Updates](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks.html)
  * 刪除: stack 中所有資源將被刪除，如需保留，可以利用 [Deletion Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-attribute-deletionpolicy.html)

## [Setting Up](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/settingup.html)

* [Controlling Access with IAM](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html)
  * [Manage Credentials for Applications Running on Amazon EC2 Instances](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html#using-iam-template-manage-creds)
* [AWS CloudFormation Limits](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cloudformation-limits.html)

### Getting Started with AWS CloudFormation

* 利用 [AWS CloudFormation Sample Template Library](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/GettingStarted.html) 中的 template 建立 stack
  * [JSON format](https://s3-us-west-2.amazonaws.com/cloudformation-templates-us-west-2/WordPress_Single_Instance.template)
  * [YAML format](https://s3-us-west-2.amazonaws.com/cloudformation-templates-us-west-2/WordPress_Single_Instance.YAML)
  * key pair 手動建立
* [Template 基礎知識](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/gettingstarted.templatebasics.html#gettingstarted.templatebasics.parameters)
* [Walkthrough: Updating a Stack](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/updating.stacks.walkthrough.html#updating.create.initial.stack)
  * copy A Simple Application
  * upload template to cloudformation
  * 取名為**`UpdateTutorial`**
  * 修改 template，增加 echo
  * 選擇原有 stack, update stack
  * 功能
    * 變更程式
    * 變更資源屬性
    * 增加資源屬性 key pair
    * 變更 stack 資源

## [Best Practices](https://docs.aws.amazon.com/en_us/AWSCloudFormation/latest/UserGuide/best-practices.html) <a id="best-practices"></a>

## [Continuous Delivery with CodePipeline](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/continuous-delivery-codepipeline.html)

自動 build, test, [CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/) 可自動對 template 處理這些事項

### Walkthrough: Building a Pipeline for Test and Production Stacks

pipeline 分為 3 個階段，每個階段至少要有一個 action，依照你的 artifacts 進行

Note: S3 所有版本須清空後才可刪除 `The bucket you tried to delete is not empty. You must delete all versions in the bucket. (Service: Amazon S3; Status Code: 409; Error Code: BucketNotEmpty; Request ID: 7AFF6F42CAA14174; S3 Extended Request ID: 7+geM2Xm+KaKhIty0J0oEbx6FexpXhhAYAzvQvxh5IaxFynsGTb0wjR12SImtJFkswQ86p6vhaY=)`

1. pipeline 取得 artifacts\(template + 設定檔\)
2. 建立 test stack，等待你的核可
3. 建立 change set，等待你的核可

#### step1 編輯  artifact 並上傳到 S3

CodePipeline artifact 須打包成 zip 後上傳到 S3

1. 下載[範例](https://s3.amazonaws.com/cloudformation-examples/user-guide/continuous-deployment/wordpress-single-instance.zip)，含 wordpress template, test stack 設定檔, production stack 設定檔
2. 解壓縮後編輯
3. 重新打包
4. 上傳到 S3, versioning enabled

#### step2 建立 pipline stack

1. 下載[範例](https://s3.amazonaws.com/cloudformation-examples/user-guide/continuous-deployment/basic-pipeline.yml.)
2. CloudFormation 建立 stack
3. 上傳範例 basic-pipeline.yml
4. stack name: `sample-WordPress-pipeline`

## Working with Stacks

stack: 一群可管理的 AWS resources，可進行 CRUD

## [CloudFormation API](https://docs.aws.amazon.com/zh_tw/AWSCloudFormation/latest/APIReference/Welcome.html)

運用 template 管理 AWS infra

* stacks: 運用資源的單位，用 template 來建立、修改、刪除一群的資源
* change sets: 變更運作中的資源，查看對現有資源的影響
* stack sets: 跨 account

