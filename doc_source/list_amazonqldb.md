# Actions, Resources, and Condition Keys for Amazon QLDB<a name="list_amazonqldb"></a>

Amazon QLDB \(service prefix: `qldb`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/qldb/latest/developerguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/qldb/latest/developerguide/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/qldb/latest/developerguide/security-iam.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon QLDB](#amazonqldb-actions-as-permissions)
+ [Resources Defined by Amazon QLDB](#amazonqldb-resources-for-iam-policies)
+ [Condition Keys for Amazon QLDB](#amazonqldb-policy-keys)

## Actions Defined by Amazon QLDB<a name="amazonqldb-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonqldb.html)

## Resources Defined by Amazon QLDB<a name="amazonqldb-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonqldb-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ ledger ](https://docs.aws.amazon.com/qldb/latest/developerguide/what-is.html)  |  arn:$\{Partition\}:qldb:$\{Region\}:$\{Account\}:ledger/$\{LedgerName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonqldb-aws_ResourceTag___TagKey_)   | 

## Condition Keys for Amazon QLDB<a name="amazonqldb-policy-keys"></a>

Amazon QLDB defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the presence of tag key\-value pairs in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag key\-value pairs attached to the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of tag keys in the request | String | 