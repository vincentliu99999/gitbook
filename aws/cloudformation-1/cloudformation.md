# CloudFormation Doc

## [What is AWS CloudFormation?](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html)

### **AWS CloudFormation Concepts**

* 使用 template 描述運用的 AWS 資源及屬性
* 簡化 Infraructure 管理，免個別設定，省時省力省複雜度
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

### [Do Not Embed Credentials in Your Templates](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html#creds)

## [Continuous Delivery with CodePipeline](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/continuous-delivery-codepipeline.html)

自動 build, test, [CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/) 可自動對 template 處理這些事項

### Walkthrough: Building a Pipeline for Test and Production Stacks \(pending\)

pipeline 分為 3 個階段，每個階段至少要有一個 action，依照你的 artifacts 進行

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

## [Working with Stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html)

stack: 一群可管理的 AWS resources，並可視為一個單位，stack 可進行 create, update, delete，皆由 template 定義，CloudFormation 確保所有單位皆須運作正常，否則會進行 roll back

### [Using the Console](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-using-console.html)

[console](https://console.aws.amazon.com/cloudformation/)

#### [Creating a Stack](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-create-stack.html)

準備 template

* template 已準備好
  * 1. Amazon S3 URL，如果有啟用版本，可以指定
    2. 手動上傳，上限 460,800 bytes，上傳後會有 S3 URL
* [template 範本](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-sample-templates.html)，由 CloudFormation 提供，現有資源可以用 `CloudFormer` 建立 stack
* [Designer](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/working-with-templates-cfn-designer.html): 可用拖拉方式編輯

準備名稱及[參數](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html)客製化建立 template

* 可在 template 準備參數值選項
* 參數可有預設值
* AWS 特定參數，可用 drop down list 選擇，例如 `AWS::EC2::VPC::Id` 就可以選擇或搜尋 VPC

#### [設定 stack 選項](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-add-tags.html)

* tag
* [權限](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-servicerole.html) by IAM
* Stack policy: [預防無預警 update](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/protect-stack-resources.html)
* Rollback 設定: by Cloudwatch alarms [monitor](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-rollback-triggers.html)
* 通知選項: by SNS
* 建立選項
  * Rollback on failure: 預設開啟，debug 時可關閉
  * Timeout: 預設無, 個別資源可能有設定
  * Termination protection: 預設關閉，[避免無預警刪除](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-protect-stacks.html)

#### [檢視 stack 資料及資源](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-view-stack-data-resources.html)

* **Stack info**
* \*\*\*\*[**Stack Status Codes**](https://docs.aws.amazon.com/zh_tw/AWSCloudFormation/latest/UserGuide/cfn-console-view-stack-data-resources.html#cfn-console-view-stack-data-resources-status-codes)\*\*\*\*

#### \*\*\*\*[**URL 快速建立**](https://docs.aws.amazon.com/zh_tw/AWSCloudFormation/latest/UserGuide/cfn-console-create-stacks-quick-create-links.html)\*\*\*\*

* templateURL
* stackName
* 參數
  * param\__`parameterName`_
  * NoEcho 會忽略

```text
https://eu-central-1.console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/create/review
   ?templateURL=https://s3-eu-central-1.amazonaws.com/cloudformation-templates-eu-central-1/WordPress_Single_Instance.template
   &stackName=MyWPBlog
   &param_DBName=mywpblog
   &param_InstanceType=t2.medium
   &param_KeyName=MyKeyPair
```

#### 刪除 Stack

* DELETE\_IN\_PROGRESS -&gt; DELETE\_COMPLETE
* DELETE\_FAILED [原因](https://docs.aws.amazon.com/zh_tw/AWSCloudFormation/latest/UserGuide/troubleshooting.html#troubleshooting-errors-delete-stack-fails) 

### [Using the AWS CLI](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-using-cli.html)

### [更新 stack](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks.html)

1. 直接更新\(較快速\)
2. 建立 change set，可預覽變更、選擇是否要套用\(考慮選項時\)

#### 更新行為

不同 resource 有不同行為，參閱  [AWS Resource Types Reference](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html)

1. 不中斷 ex: AWS::CloudTrail::Trail
2. 中斷 ex: AWS::EC2::Instance
3. 取代 ex: AWS::RDS::DBInstance

#### 更新 stack template

更新資源及屬性，用以存在的 template 來更新

變更參數或設定時，不需更新 template

1. 選擇 stack
2. view in designer
3. 修改 template
4. 驗證 template
5. 儲存

## [Bringing Existing Resources Into CloudFormation Management](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/resource-import.html)\(pending\)

用 change set 匯入已存在資源至 stack，或建立新的 stack [Resource Import Status Codes](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/resource-import.html#resource-import-status-codes)

* 用 template 描述，匯入的資源需指定 [DeletionPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-attribute-deletionpolicy.html)
* 資源識別屬性、值

資源匯入驗證

* 資源必須存在
* 屬性及設定選項
* [必要的屬性](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html)
* 不存在其他 stack

匯入作業

* 針對匯入資源 run [drift detection](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/detect-drift-stack.html)，確保設定
* 匯入過程不允許資源的建立、刪除、修改設定

## Working with AWS CloudFormation Templates <a id="template-guide"></a>

JSON, YAML 格式的文字檔，或用 designer，可參閱 [Template Snippets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/CHAP_TemplateQuickRef.html)

### Template Formats

YAML 可有註解，但之後用 Designer 編輯後註解會消失

* [ECMA-404 JSON](http://www.json.org/)
* [YAML Version 1.1](http://www.yaml.org/)，但有部分功能不支援

### 解析 Template

僅有 `Resources` 區段是必要的，因有數值會做參照，建議區段順序下如下

1. [Format Version \(optional\)](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/format-version-structure.html) 目前僅有 `2010-09-09` 是合法的，沒設定會用最新版
2. [Description \(optional\)](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-description-structure.html) 描述 template
3. [Metadata \(optional\)](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/metadata-section-structure.html)
4. [Parameters \(optional\)](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html) 可參照 `Resources` 以及 `Outputs`
   1. 在 template 中定義
   2. 可參照變數
   3. 最多 60 個，[Type](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html#parameters-section-structure-properties-type) 必須是支援的、執行過程需指定數值、僅能參照同個檔案的變數
   4. \*\*\*\*[Properties](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html#parameters-section-structure-properties)
   5. [AWS 特定參數類型](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html#aws-specific-parameter-types)
   6. [SSM Parameter Types](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html#parameters-section-ssm-examples) 直接使用  [Systems Manager Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-paramstore.html) 作為變數來源，ref: [https://docs.aws.amazon.com/zh\_tw/systems-manager/latest/userguide/sysman-paramstore-securestring.html](https://docs.aws.amazon.com/zh_tw/systems-manager/latest/userguide/sysman-paramstore-securestring.html)
   7. console 介面預設會依照字母順序排序，可在 `AWS::CloudFormation::Interface` 變更
5. [Mappings \(optional\)](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/mappings-section-structure.html) 條件式參數，可利用 [Fn::FindInMap](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-findinmap.html)
6. [Conditions \(optional\)](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/conditions-section-structure.html) 可 include 任意的 JSON 或 YAML 物件，詳細描述 template\(pending\)
   1. [AWS::CloudFormation::Authentication](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-authentication.html)
   2. [AWS::CloudFormation::Init](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-init.html)
   3. [AWS::CloudFormation::Interface](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudformation-interface.html)
7. [Transform \(optional\)](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/transform-section-structure.html) for [serverless applications](https://docs.aws.amazon.com/lambda/latest/dg/deploying-lambda-apps.html)
8. [Resources \(required\)](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/resources-section-structure.html)
9. [Outputs \(optional\)](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/outputs-section-structure.html) 查看 stack 的屬性要顯示什麼

## [故障診斷](https://docs.aws.amazon.com/zh_tw/AWSCloudFormation/latest/UserGuide/troubleshooting.html)

### 刪除堆疊失敗

* 須清空的資源
  * S3 所有版本須清空後才可刪除

{% hint style="info" %}
`The bucket you tried to delete is not empty. You must delete all versions in the bucket. (Service: Amazon S3; Status Code: 409; Error Code: BucketNotEmpty; Request ID: 7AFF6F42CAA14174; S3 Extended Request ID: 7+geM2Xm+KaKhIty0J0oEbx6FexpXhhAYAzvQvxh5IaxFynsGTb0wjR12SImtJFkswQ86p6vhaY=)`
{% endhint %}

## [CloudFormation API](https://docs.aws.amazon.com/zh_tw/AWSCloudFormation/latest/APIReference/Welcome.html)

運用 template 管理 AWS infra

* stacks: 運用資源的單位，用 template 來建立、修改、刪除一群的資源
* change sets: 變更運作中的資源，查看對現有資源的影響
* stack sets: 跨 account

