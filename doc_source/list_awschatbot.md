# Actions, Resources, and Condition Keys for AWS Chatbot<a name="list_awschatbot"></a>

AWS Chatbot \(service prefix: `chatbot`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by AWS Chatbot](#awschatbot-actions-as-permissions)
+ [Resources Defined by AWS Chatbot](#awschatbot-resources-for-iam-policies)
+ [Condition Keys for AWS Chatbot](#awschatbot-policy-keys)

## Actions Defined by AWS Chatbot<a name="awschatbot-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   CreateChimeWebhookConfiguration  | Creates an AWS Chatbot Chime Webhook Configuration\. | Write |  |  |  | 
|   CreateSlackChannelConfiguration  | Creates an AWS Chatbot Slack Channel Configuration\. | Write |  |  |  | 
|   DeleteChimeWebhookConfiguration  | Deletes an AWS Chatbot Chime Webhook Configuration\. | Write |  |  |  | 
|   DeleteSlackChannelConfiguration  | Deletes an AWS Chatbot Slack Channel Configuration\. | Write |  |  |  | 
|   DescribeChimeWebhookConfigurations  | Lists all AWS Chatbot Chime Webhook Configurations in an AWS Account\. | Read |  |  |  | 
|   DescribeSlackChannelConfigurations  | Lists all AWS Chatbot Slack Channel Configurations in an AWS account\. | Read |  |  |  | 
|   DescribeSlackChannels  | Lists all public Slack channels in the Slack workspace connected to the AWS Account onboarded with AWS Chatbot service\. | Read |  |  |  | 
|   DescribeSlackWorkspaces  | Lists all authorized Slack workspaces connected to the AWS Account onboarded with AWS Chatbot service\. | Read |  |  |  | 
|   GetSlackOauthParameters  | Generate OAuth parameters to request Slack OAuth code to be used by the AWS Chatbot service\. | Read |  |  |  | 
|   RedeemSlackOauthCode  | Redeem previously generated parameters with Slack API, to acquire OAuth tokens to be used by the AWS Chatbot service\. | Write |  |  |  | 
|   UpdateChimeWebhookConfiguration  | Updates an AWS Chatbot Chime Webhook Configuration\. | Write |  |  |  | 
|   UpdateSlackChannelConfiguration  | Updates an AWS Chatbot Slack Channel Configuration\. | Write |  |  |  | 

## Resources Defined by AWS Chatbot<a name="awschatbot-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awschatbot-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   ChatbotConfiguration  |  arn:$\{Partition\}:chatbot::$\{account\}:$\{resourceType\}/$\{resourceName\}  |  | 

## Condition Keys for AWS Chatbot<a name="awschatbot-policy-keys"></a>

Chatbot has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.