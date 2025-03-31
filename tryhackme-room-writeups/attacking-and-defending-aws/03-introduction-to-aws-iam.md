---
layout: ../../../../../layouts/MarkdownLayout.astro
roomName: Introduction to AWS IAM
title: 'THM - Introduction to AWS IAM'
description: 'Walkthrough of the Introduction to AWS IAM room'
learningPath: Attacking and Defending AWS
image:
  url: '/blog-images/introduction-to-aws-iam.png'
  alt: 'Cloud graphic with Introduction to AWS IAM room name and TryHackMe logo.'
---

Here is my written walkthrough of the third room in the TryHackMe **[Attacking and Defending AWS](https://tryhackme.com/path/outline/attackinganddefendingaws)** learning path. This room introduces us to AWS Identity and Access Management (IAM).

> **✨📺**
> If you want to see some extremely cringe youtube-ing, check out my [video walkthrough](https://youtu.be/VDe92PyEUcg?si=Ak4xR8uTMFA31Syt) of this room.

## About this room

This room provides a foundational understanding of AWS IAM, which is crucial for both security professionals and developers working with AWS. While it's still mostly reading and answering questions, it sets up important concepts that we practice hands on in upcoming rooms. If you're new to IAM, the room is good introduction (IMO) and if you are experienced with IAM, it's still a great refresher. It doesn't take long to complete.

## Tasks

### Task 1 - Why is IAM so important?

Here we learn why IAM is critical in AWS security. We learn several IAM key concepts:

&star; **IAM Principals**: The "who" that can act in your AWS account (people, applications, and AWS services)
&star; **IAM Policies**: Define what a principal can do
&star; **IAM Credentials**: How principals authenticate to the AWS control plane (APIs) to use their permissions and do actions
&star; **Least Privilege**: The concept of giving principals only the permissions they absolutely need - not as easy as you might think!

> **NOTE**
> Using misconfigured or overly permissive IAM resources is a key tactic for privilege escalation in cloud environments. We learn more about this later in the learning path.

The room uses a nice metaphor about castles to contrast traditional network security vs. cloud security:
- **🏰 Traditional network security**: You're either inside or outside a firewall or, in the case of a castle, a secured perimeter defending against incoming armies on the ground
- **🐉 Cloud security**: cloud infrastructure is managed using APIs over the internet, as a defender, you need to protect your cloud environment from API calls that can control your entire infrastructure. THM compares this to a dragon flying at the castle from the sky.

🚩 There is no question or flag - we simply pledge our allegiance to the importance of AWS IAM and then move on to task 2.

### Task 2 - Introduction to AWS IAM

This task dives deeper into the core concepts of IAM:

&star; **AWS Account**: The fundamental trust boundary in AWS. Each account is treated as an independent customer (not sure this is 100% true anymore - but there is certainly a distinct separation between every unique account).
&star; **Root User**: The all-powerful, God-mode user that comes with every AWS account. Best practice is to use the root user as little as possible.
&star; **IAM Users**: Type of IAM principal - often mapped to a human person. Policies can be attached to users to give users permission. If the user has something called a `Login Profile`, a human can use the IAM user credentials to log in to the AWS console.
  > **NOTE**
  > Really, (IMHO) it is rare that IAM Users should be used to directly grant permissions to AWS resources. Nowadays, the best practice is to either have no users, or have IAM users who have tightly controlled permissions to assume IAM roles. This is because IAM users are accessed with long-lived credentials - which are generally more dangerous than short-term credentials.
&star; **IAM Groups**: Type of IAM principal. Users can be organized in groups and policies can be applied at the group level. THM doesn't cover this yet in the room but I'm going rogue and mentioning it here anyway.
&star; **IAM Roles**: Another type of IAM principal, IAM policies can be attached to IAM roles to grant permissions. Roles are better than users because they **TEMPORARILY** delegate authentication and identity to another principal. Roles don't use long-lived credentials. Traditionally people often think of roles as attached to a machine workload instead of a human. For example an EC2 instance (server) running a script using an IAM role to gain permissions to download an object out of an S3 bucket.
&star; **IAM Policies**: Required for both users and roles to do anything. By default, all API requests are **implicitly denied**.

We also learn about **ARNs**. Amazon Resource Names (ARNs) uniquely identify AWS resources. ARNs are highly intertwined with IAM because they are often used in IAM policies to grant permissions to specific AWS resources (the more specific the better).

Arns are constructed with a specific structure. The arn consists of 

&star; Service, 
&star; AWS Region
&star; AWS Account ID
&star; identifiers for the Resource, 

Here are a couple of examples (slightly tweaked from the examples THM uses):

**ARN format for EC2 instance**
`arn:aws:<service>:<region>:<AWS account ID>:instance/<ec2 instance ID>`

**Example EC2 instance ARN**
`arn:aws:ec2:us-east-1:123456789012:instance/i-00c07e4f8c9f9bsk3`

**ARN format for EC2 instance**
`arn:aws:<service>::<AWS account ID>:role/admin-role`

**Example IAM Role ARN**
`arn:aws:iam::123456789012:role/account-admin`

> **🌎NOTE**
> IAM Arns do not include the region because, as we learned earlier, IAM is a global service. Note the two colons in a row between :<service>::<AWS account ID>:. This is the gap where region would be.

This ARN format is true for `AWS` commercial aws partition. Partitions are parts of AWS have a `hard boundary` between each other. Most people are almost always using the `AWS` partition, but there are other specifical partitions for government and for China. ARNs for other partitions will not start with `arn:aws:`. For example, whilst I have never seen one with my own eyes, I think the China partition ARNs would start with `arn:aws-cn:` because `aws-cn` identifies the China partition.

🚩 Again there is no question or flag - we simply click **Complete** when we are ready to move on to the next room.