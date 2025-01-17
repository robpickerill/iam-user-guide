# Policies and Permissions<a name="access_policies"></a>

You manage access in AWS by creating policies and attaching them to IAM identities \(users, groups of users, or roles\) or AWS resources\. A policy is an object in AWS that, when associated with an identity or resource, defines their permissions\. AWS evaluates these policies when a principal entity \(user or role\) makes a request\. Permissions in the policies determine whether the request is allowed or denied\. Most policies are stored in AWS as JSON documents\. AWS supports six types of policies: identity\-based policies, resource\-based policies, permissions boundaries, Organizations SCPs, ACLs, and session policies\.

IAM policies define permissions for an action regardless of the method that you use to perform the operation\. For example, if a policy allows the [GetUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html) action, then a user with that policy can get user information from the AWS Management Console, the AWS CLI, or the AWS API\. When you create an IAM user, you can choose to allow console or programmatic access\. If console access is allowed, the IAM user can sign in to the console using a user name and password\. Or if programmatic access is allowed, the user can use access keys to work with the CLI or API\.

## Policy Types<a name="access_policy-types"></a>

The following policy types, listed in order of frequency, are available for use in AWS\. For more details, see the sections below for each policy type\.
+ **[Identity\-based policies](#policies_id-based)** – Attach managed and inline policies to IAM identities \(users, groups to which users belong, or roles\)\. Identity\-based policies grant permissions to an identity\.
+ **[Resource\-based policies](#policies_resource-based)** – Attach inline policies to resources\. The most common examples of resource\-based policies are Amazon S3 bucket policies and IAM role trust policies\. Resource\-based policies grant permissions to a principal entity that is specified in the policy\. Principals can be in the same account as the resource or in other accounts\.
+ **[Permissions boundaries](#policies_bound)** – Use a managed policy as the permissions boundary for an IAM entity \(user or role\)\. That policy defines the maximum permissions that the identity\-based policies can grant to an entity, but does not grant permissions\. Permissions boundaries do not define the maximum permissions that a resource\-based policy can grant to an entity\.
+ **[Organizations SCPs](#policies_scp)** – Use an AWS Organizations service control policy \(SCP\) to define the maximum permissions for account members of an organization or organizational unit \(OU\)\. SCPs limit permissions that identity\-based policies or resource\-based policies grant to entities \(users or roles\) within the account, but do not grant permissions\.
+ **[Access control lists \(ACLs\)](#policies_acl)** – Use ACLs to control which principals in other accounts can access the resource to which the ACL is attached\. ACLs are similar to resource\-based policies, although they are the only policy type that does not use the JSON policy document structure\. ACLs are cross\-account permissions policies that grant permissions to the specified principal entity\. ACLs cannot grant permissions to entities within the same account\.
+ **[Session policies](#policies_session)** – Pass advanced session policies when you use the AWS CLI or AWS API to assume a role or a federated user\. Session policies limit the permissions that the role or user's identity\-based policies grant to the session\. Session policies limit permissions for a created session, but do not grant permissions\. For more information, see [Session Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#policies_session)\.

### Identity\-Based Policies<a name="policies_id-based"></a>

Identity\-based policies are JSON permissions policy documents that you can attach to an identity \(user, group of users, or role\)\. These policies control what actions an entity \(user or role\) can perform, on which resources, and under what conditions\. Identity\-based policies can be further categorized:
+ **Managed policies** – Standalone identity\-based policies that you can attach to multiple users, groups, and roles in your AWS account\. You can use two types of managed policies: 
  + **AWS managed policies** – Managed policies that are created and managed by AWS\. If you are new to using policies, we recommend that you start by using AWS managed policies\.
  + **Customer managed policies** – Managed policies that you create and manage in your AWS account\. Customer managed policies provide more precise control over your policies than AWS managed policies\. You can create and edit an IAM policy in the visual editor or by creating the JSON policy document directly\. For more information, see [Creating IAM Policies](access_policies_create.md) and [Editing IAM Policies](access_policies_manage-edit.md)\.
+ **Inline policies** – Policies that you create and manage and that are embedded directly into a single user, group, or role\. In most cases, we don't recommend using inline policies\.

To learn how to choose between a managed policy or an inline policy, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\.

### Resource\-Based Policies<a name="policies_resource-based"></a>

Resource\-based policies are JSON policy documents that you attach to a resource such as an Amazon S3 bucket\. These policies grant the specified principal permission to perform specific actions on that resource and defines under what conditions this applies\. Resource\-based policies are inline policies\. There are no managed resource\-based policies\. 

To enable cross\-account access, you can specify an entire account or IAM entities in another account as the principal in a resource\-based policy\. Adding a cross\-account principal to a resource\-based policy is only half of establishing the trust relationship\. When the principal and the resource are in separate AWS accounts, you must also use an identity\-based policy to grant the principal entity access to the resource\. However, if a resource\-based policy grants access to a principal in the same account, no additional identity\-based policy is required\.

The IAM service supports only one type of resource\-based policy called a role *trust policy*, which is attached to an IAM role\. An IAM role is both an identity and a resource that supports resource\-based policies\. For that reason, you must attach both a trust policy and an identity\-based policy to an IAM role\. Trust policies define which principal entities \(accounts, users, roles, and federated users\) can assume the role\. To learn how IAM roles are different from other resource\-based policies, see [How IAM Roles Differ from Resource\-based Policies](id_roles_compare-resource-policies.md)\.

To see which other services support resource\-based policies, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md)\. To learn more about resource\-based policies, see [Identity\-Based Policies and Resource\-Based Policies](access_policies_identity-vs-resource.md)\. 

### IAM Permissions Boundaries<a name="policies_bound"></a>

A permissions boundary is an advanced feature in which you set the maximum permissions that an identity\-based policy can grant to an IAM entity\. When you set a permissions boundary for an entity, the entity can perform only the actions that are allowed by both its identity\-based policies and its permissions boundaries\. Resource\-based policies that specify the user or role as the principal are not limited by the permissions boundary\. An explicit deny in any of these policies overrides the allow\. For more information about permissions boundaries, see [Permissions Boundaries for IAM Entities](access_policies_boundaries.md)\.

### Service Control Policies \(SCPs\)<a name="policies_scp"></a>

AWS Organizations is a service for grouping and centrally managing the AWS accounts that your business owns\. If you enable all features in an organization, then you can apply service control policies \(SCPs\) to any or all of your accounts\. SCPs are JSON policies that specify the maximum permissions for an organization or organizational unit \(OU\)\. The SCP limits permissions for entities in member accounts, including each AWS account root user\. An explicit deny in any of these policies overrides the allow\.

For more information about Organizations and SCPs, see [About Service Control Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_about-scps.html) in the *AWS Organizations User Guide*\.

### Access Control Lists \(ACLs\)<a name="policies_acl"></a>

Access control lists \(ACLs\) are service policies that allow you to control which principals in another account can access a resource\. ACLs cannot be used to control access for a principal within the same account\. ACLs are similar to resource\-based policies, although they are the only policy type that does not use the JSON policy document format\. Amazon S3, AWS WAF, and Amazon VPC are examples of services that support ACLs\. To learn more about ACLs, see [Access Control List \(ACL\) Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.

### Session Policies<a name="policies_session"></a>

Session policies are advanced policies that you pass in a parameter when you programmatically create a temporary session for a role or federated user\. The permissions for a session are the intersection of the identity\-based policies for the IAM entity \(user or role\) used to create the session and the session policies\. Permissions can also come from a resource\-based policy\. An explicit deny in any of these policies overrides the allow\.

You can create role session and pass session policies programmatically using the `AssumeRole`, `AssumeRoleWithSAML`, or `AssumeRoleWithWebIdentity` API operations\. You can pass a single JSON inline session policy document using the `Policy` parameter\. You can use the `PolicyArns` parameter to specify up to 10 managed session policies\. For more information about creating a role session, see [Requesting Temporary Security Credentials](id_credentials_temp_request.md)\.

When you create a federated user session, you use an IAM user's access keys to programmatically call the `GetFederationToken` API operation\. You must also pass session policies\. The resulting session's permissions are the intersection of the IAM user's identity\-based policy and the session policy\. For more information about creating a federated user session, see [[GetFederationToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)—Federation Through a Custom Identity Broker](id_credentials_temp_request.md#api_getfederationtoken)\.

A resource\-based policy can specify the ARN of the user or role as a principal\. In that case, the permissions from the resource\-based policy are added to the role or user's identity\-based policy before the session is created\. The session policy limits the total permissions granted by the resource\-based policy and the identity\-based policy\. The resulting session's permissions are the intersection of the session policies and either the resource\-based policy or the identity\-based policy\.

![\[Evaluation of the session policy with a resource-based policy specifying the entity ARN\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/EffectivePermissions-session-rbp-id.png)

A resource\-based policy can specify the ARN of the session as a principal\. In that case, the permissions from the resource\-based policy are added after the session is created\. The resource\-based policy permissions are not limited by the session policy\. The resulting session has all the permissions of the resource\-based policy *plus* the intersection of the identity\-based policy and the session policy\.

![\[Evaluation of the session policy with a resource-based policy specifying the session ARN\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/EffectivePermissions-session-rbpsession-id.png)

A permissions boundary can set the maximum permissions for a user or role that is used to create a session\. In that case, the resulting session's permissions are the intersection of the session policy, the permissions boundary, and the identity\-based policy\. However, a permissions boundary does not limit permissions granted by a resource\-based policy that specifies the ARN of the resulting session\.

![\[Evaluation of the session policy with a permissions boundary\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/EffectivePermissions-session-boundary-id.png)

## Policies and the Root User<a name="access_policies-root"></a>

The AWS account root user is affected by some policy types but not others\. You cannot attach identity\-based policies to the root user, and you cannot set the permissions boundary for the root user\. However, you can specify the root user as the principal in a resource\-based policy or an ACL\. As a member of an account, the root user is affected by any SCPs for the account\.

## Overview of JSON Policies<a name="access_policies-json"></a>

Most policies are stored in AWS as JSON documents\. Identity\-based policies and policies used to set permissions boundaries are JSON policy documents that you attach to a user or role\. Resource\-based policies are JSON policy documents that you attach to a resource\. SCPs are JSON policy documents with restricted syntax that you attach to an AWS Organizations organizational unit \(OU\)\. ACLs are also attached to a resource, but you must use a different syntax\. Session policies are JSON policies that you provide when you assume a role or federated user session\.

It is not necessary for you to understand the JSON syntax\. You can use the visual editor in the AWS Management Console to create and edit customer managed policies without ever using JSON\. However, if you use inline policies for groups or complex policies, you must still create and edit those policies in the JSON editor using the console\. For more information about using the visual editor, see [Creating IAM Policies](access_policies_create.md) and [Editing IAM Policies](access_policies_manage-edit.md)\.

### JSON Policy Document Structure<a name="policies-introduction"></a>

As illustrated in the following figure, a JSON policy document includes these elements:
+ Optional policywide information at the top of the document
+ One or more individual statements**

Each statement includes information about a single permission\. If a policy includes multiple statements, AWS applies a logical `OR` across the statements when evaluating them\. If multiple policies apply to a request, AWS applies a logical `OR` across all of those policies when evaluating them\. 

![\[JSON policy document structure\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_General_Policy_Structure.diagram.png)

The information in a statement is contained within a series of elements\.
+ **Version** – Specify the version of the policy language that you want to use\. As a best practice, use the latest `2012-10-17` version\.
+ **Statement** – Use this main policy element as a container for the following elements\. You can include more than one statement in a policy\.
+ **Sid** – Include an optional statement ID to differentiate between your statements\.
+ **Effect** – Use `Allow` or `Deny` to indicate whether the policy allows or denies access\.
+ **Principal** – Indicate the account, user, role, or federated user to which you would like to allow or deny access\. If you are creating a policy to attach to a user or role, you cannot include this element\. The principal is implied as that user or role\.
+ **Action** – Include a list of actions that the policy allows or denies\.
+ **Resource** – Specify a list of resources to which the actions apply\.
+ **Condition** \(Optional\) – Specify the circumstances under which the policy grants permission\.

To learn about these and other more advanced policy elements, see [IAM JSON Policy Elements Reference](reference_policies_elements.md)\. 

### Multiple Statements and Multiple Policies<a name="policies-syntax-multiples"></a>

If you want to define more than one permission for an entity \(user, group, or role\), you can use multiple statements in a single policy\. You can also attach multiple policies\. If you try to define multiple permissions in a single statement, your policy might not grant the access that you expect\. As a best practice, break up policies by resource type\. 

Because of the [limited size of policies](reference_iam-limits.md), it might be necessary to use multiple policies for more complex permissions\. It's also a good idea to create functional groupings of permissions in a separate customer managed policy\. For example, Create one policy for IAM user management, one for self\-management, and another policy for S3 bucket management\. Regardless of the combination of multiple statements and multiple policies, AWS [evaluates](reference_policies_evaluation-logic.md) your policies the same way\.

For example, the following policy has three statements, each of which defines a separate set of permissions within a single account\. The statements define the following:
+ The first statement, with an `Sid` \(Statement ID\) of `FirstStatement`, lets the user with the attached policy change their own password\. The `Resource` element in this statement is "`*`" \(which means "all resources"\)\. But in practice, the `ChangePassword` API operation \(or equivalent `change-password` CLI command\) affects only the password for the user who makes the request\. 
+ The second statement lets the user list all the Amazon S3 buckets in their AWS account\. The `Resource` element in this statement is `"*"` \(which means "all resources"\)\. But because policies don't grant access to resources in other accounts, the user can list only the buckets in their own AWS account\. 
+ The third statement lets the user list and retrieve any object that is in a bucket named `confidential-data`, but only when the user is authenticated with multi\-factor authentication \(MFA\)\. The `Condition` element in the policy enforces the MFA authentication\.

  When a policy statement contains a `Condition` element, the statement is only in effect when the `Condition` element evaluates to true\. In this case, the `Condition` evaluates to true when the user is MFA\-authenticated\. If the user is not MFA\-authenticated, this `Condition` evaluates to false\. In that case, the third statement in this policy does not apply and the user does not have access to the `confidential-data` bucket\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "FirstStatement",
      "Effect": "Allow",
      "Action": ["iam:ChangePassword"],
      "Resource": "*"
    },
    {
      "Sid": "SecondStatement",
      "Effect": "Allow",
      "Action": "s3:ListAllMyBuckets",
      "Resource": "*"
    },
    {
      "Sid": "ThirdStatement",
      "Effect": "Allow",
      "Action": [
        "s3:List*",
        "s3:Get*"
      ],
      "Resource": [
        "arn:aws:s3:::confidential-data",
        "arn:aws:s3:::confidential-data/*"
      ],
      "Condition": {"Bool": {"aws:MultiFactorAuthPresent": "true"}}
    }
  ]
}
```

### Examples of JSON Policy Syntax<a name="policies-syntax-examples"></a>

The following identity\-based policy allows the implied principal to list a single Amazon S3 bucket named `example_bucket`: 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "s3:ListBucket",
    "Resource": "arn:aws:s3:::example_bucket"
  }
}
```

The following resource\-based policy can be attached to an Amazon S3 bucket\. The policy allows members of a specific AWS account to perform any Amazon S3 actions in the bucket named `mybucket`\. It allows any action that can be performed on a bucket or the objects within it\. \(Because the policy grants trust only to the account, individual users in the account must still be granted permissions for the specified Amazon S3 actions\.\) 

```
{
  "Version": "2012-10-17",
  "Id": "S3-Account-Permissions",
  "Statement": [{
    "Sid": "1",
    "Effect": "Allow",
    "Principal": {"AWS": ["arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:root"]},
    "Action": "s3:*",
    "Resource": [
      "arn:aws:s3:::mybucket",
      "arn:aws:s3:::mybucket/*"
    ]
  }]
}
```

To view example policies for common scenarios, see [Example IAM Identity\-Based Policies](access_policies_examples.md)\. 