# Creating an IAM user

When you create an AWS account, you register with an email address and you create a password. 
This account becomes the root user of the AWS account. 

This root user has full access to perform any action in the account. 
Using an account with unrestricted access to perform routine and day-to-day adiministrative task poses a high security risk.


KEEP IT SHORT
******
What is IAM

AWS IAM manages the login credentials and permissions to the AWS account

AWS Identity and Access Management (IAM) is an AWS service that helps you manage access to your AWS account and resources
Any AWS customer can use IAM; the service is offered at no additional charge.

IAM allows you to create users and each individual person who needs access to your AWS account would have their own unique IAM user. 


IAM user
An IAM user represents a person or service that interacts with AWS. You define the user in your AWS account. (Replace with Azure definition)


IAM provides both Authentication and Authorization

Authentication being verifying if someone is who they say they are because they had the proper credentials to log in

After loggin in, Authorization determines which actions you can perform in the account

and you can take care of authorization by attaching IAM policies to users in order to grant or deny permission to specific actions within an AWS account.

IAM policies are JSON-based documents. Let's take a look at an example. This IAM policy document contains permissions that allow the identity to which it's attached to perform any EC2-related action. The structure of an IAM policy has an Effect which is either allow or deny, and Action

IAM policies can be attached to IAM groups 

IAM groups are very simply just groupings of IAM users.

Instead of creating and associating muliple policies to multiple users, with IAM groups, you can attach a single policy to a 
Group of users requiring the same accesss. 


Why go through the hassle of creating an IAM user, can't I just use the root user. 

The reason we suggest you do this is because you cannot apply a policy to the root user, but you can to an IAM user.
It enables you to implement principle of leat priviledge. (Only working with only the necessary permissions to accomplish a task.)


Now that you have a basic Idea (Now that we have explored some basic jargon regarding IAM, let us create an IAM user we can use to administer other IAM users.  )

Then create an IAM user with admin permissions. 


**********

Steps to create an IAM user:

1. 
2. 
3. 

NOTE: MFA prompt can be skipped for now.
etc. . . .