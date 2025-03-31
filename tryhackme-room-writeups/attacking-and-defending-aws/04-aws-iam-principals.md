---
layout: ../../../../../layouts/MarkdownLayout.astro
roomName: AWS IAM Principals
title: 'THM - AWS IAM Principals'
description: 'Walkthrough of the AWS IAM Principals room'
learningPath: Attacking and Defending AWS
pubDate: Tod
image:
  url: '/blog-images/aws-iam-principals.png'
  alt: 'Cloud graphic with AWS IAM Principals room name and TryHackMe logo.'
---

Welcome to the fourth room in the **[Attacking and Defending AWS](https://tryhackme.com/path/outline/attackinganddefendingaws)** learning path! This room focuses on IAM Principals, which are the "who" in AWS security - the entities that can act in your AWS account. This is a crucial concept for both attackers and defenders to understand, as it's the foundation of AWS access control.

> **✨📺**
> If you want to see my video walkthrough of this room, check it out [here](https://youtu.be/bqayurUj1bU?si=AfXwj2vPU_J3lgsN).

## About this room

This room provides hands-on experience with AWS IAM principals in a sandbox environment. For the first time in the learning path, we get to interact with a real AWS account! The room covers different types of IAM principals and their significance for both attack and defense strategies.

## Tasks

### Task 1 - Introduction to IAM Principals

This task introduces the concept of IAM principals (also called IAM identities). Key points:

&star; IAM principals provide access to AWS accounts and resources
&star; They handle authentication and validate that authentication was performed
&star; They are core concepts for resource policies
&star; They represent the "who" in AWS security

> <div class="flag-toggle">🚩 What are IAM principals sometimes referred to as?</div>
> 
> <div class="flag-content">
> <code>IAM Identities</code>
> </div>

### Task 2 - Access the Environment

This task introduces us to the sandbox AWS environment:

&star; We get access to a real AWS account for hands-on practice
&star; The environment can be generated and reset (up to 3 times per day)
&star; Credentials are provided in the credentials tab
&star; The environment is shared across multiple IAM rooms

> <div class="flag-toggle">🚩 How many times per day can you reset the environment?</div>
> 
> <div class="flag-content">
> <code>3</code>
> </div>

### Task 3 - IAM Users

This task covers IAM users in detail:

&star; IAM users are the most basic form of IAM principal
&star; They represent people or applications (though roles are preferred for applications)
&star; They exist in a single AWS account
&star; AWS acts as both the authentication and identity store
&star; Users can have:
  - A login profile (password for AWS console access)
  - Up to two access keys (for programmatic access)

> <div class="flag-toggle">🚩 What is the maximum number of access keys an IAM user can have?</div>
> 
> <div class="flag-content">
> <code>2</code>
> </div>

### Task 4 - IAM Groups

This task explores IAM groups:

&star; Groups are collections of IAM users
&star; They make it easier to manage permissions for multiple users
&star; Best practice is to attach policies to groups rather than individual users
&star; Users can belong to multiple groups

> <div class="flag-toggle">🚩 What is the best practice for managing permissions for multiple users?</div>
> 
> <div class="flag-content">
> <code>Attach policies to groups rather than individual users</code>
> </div>

### Task 5 - IAM Roles

This task focuses on IAM roles:

&star; Roles are temporary credentials for AWS services and applications
&star; They delegate authentication and identity to another system
&star; They primarily manage authorization
&star; They are preferred over IAM users for applications
&star; They have trust relationships that define who can assume them
&star; In AWS architecture diagrams, IAM roles are represented by a hard hat icon

> <div class="flag-toggle">🚩 What type of IAM principal is preferred for applications?</div>
> 
> <div class="flag-content">
> <code>IAM Roles</code>
> </div>

### Task 6 - Hands-on Practice

This task gives us hands-on experience with IAM principals:

&star; Creating and managing IAM users
&star; Creating and managing IAM groups
&star; Creating and managing IAM roles
&star; Understanding trust relationships
&star; Managing permissions and policies

> <div class="flag-toggle">🚩 What is the first step in creating an IAM user?</div>
> 
> <div class="flag-content">
> <code>Click "Add user" in the IAM console</code>
> </div>

### Task 7 - Summary

The final task provides a summary of what we've learned about IAM principals:

&star; The different types of IAM principals (users, groups, roles)
&star; When to use each type of principal
&star; Best practices for managing principals
&star; How principals relate to authentication and authorization

> <div class="flag-toggle">🚩 What is the primary purpose of IAM principals?</div>
> 
> <div class="flag-content">
> <code>To provide access to AWS accounts and resources</code>
> </div> 