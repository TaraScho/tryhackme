---
layout: ../../../../../layouts/MarkdownLayout.astro
roomName: AWS Cloud 101
title: 'THM - AWS Cloud 101'
description: 'Walkthrough of the Try Hack Me AWS Cloud 101 room'
learningPath: Attacking and Defending AWS
pubDate: Tod
image:
  url: '/blog-images/aws-cloud-101.png'
  alt: 'Cloud graphic with AWS Cloud 101 room name and TryHackMe logo.'
---

My first ever attempt to write up a TryHackMe room, let's see how it goes. This recap is about the first room in the **[Attacking and Defending AWS](https://tryhackme.com/path/outline/attackinganddefendingaws)**. I'm a big TryHackMe fan (though I rarely have enough time to play with it these days), and I'm also an obsessive AWS/AWS security person. When the THM made the Attacking and Defending AWS learning path available to individual customers a couple of years ago I was very excited to try it out. I made a series of videos walking through the rooms and I've been wanting to make some write-ups to go along with them. This is the first one!

> **✨📺NOTE📺✨**
> If you want to see some extremely cringe youtube-ing, check out my [video walkthrough](https://youtu.be/hxosqZzXc7g?si=AfXwj2vPU_J3lgsN) of this room.

## About this room

This is without a doubt the most boring room in the learning path, but it is also a necessary evil, it effectively sets the stage for folks with limited AWS experience. It's a high-level overview of cloud computing and the history of AWS. For the most part, you just read text and answer questions.

Mildly interesting but nowhere near as fun as the actual cloud attack tactics later on in the path 😈. Actually, the fact that I'm writing a recap of it at all is silly, but it would haunt me for the rest of my life if I didn't do these in order, and I am a prisoner of my own mind, so here we go!

## Tasks

### Task 1 - Introduction

Provides an intro to the room and explains the learning objectives. All you do is click **Correct Answer**.

### Task 2 - Cloud Enters the Scene

This task contrasts the `On-premise` model with `The Cloud`. TLDR and over simplification `On-Prem` is when organizations own their own IT infrastructure and `The Cloud` is when organizations pay third-parties to host their infrastructure for them.

> 🙋‍♀️ **What is IT infrastructure**
> This is things like servers, databases, storage, etc. Picture a [rack of servers](https://www.google.com/search?sca_esv=57af5e9ba273aa7a&sxsrf=AHTn8zqCTXGkLkI_q_8mjuosbqO6T3rqjA:1743209006118&q=rack+of+servers&udm=2&fbs=ABzOT_CWdhQLP1FcmU5B0fn3xuWpA-dk4wpBWOGsoR7DG5zJBsxayPSIAqObp_AgjkUGqel3rTRMIJGV_ECIUB00muput9Zp8VMKUi0ZjqPs3JlrgNjQ9rOqRdXcDwEBQ82jIzIeJKF_t4xlLNL8OlcUPXuD4mOHi5CwSvqoRYVHDp8kIKIKk9txe0fwpxc-El6CFYl-jFdhssameWHw9C9RusrnI0QBZA&sa=X&ved=2ahUKEwjbutDMh66MAxVFATQIHUZgEa0QtKgLegQIFBAB&biw=1334&bih=754&dpr=2). Servers are computers.

> 🙋‍♀️ **What are servers**
> Servers are computers. In theory, any computer could be a server, but the type of servers we are thinking of here are extra computer-y computers - they are more powerful, optimized, etc. than your typical desktop computer.

> <div class="flag-toggle">🚩 What decade did companies start having widespread reliance on internet-connected services?</div>
> 
> <div class="flag-content">
> The answer is <code>1990s</code>. You can find this by reading the paragraph above the question (I'll be writing that a lot in this walkthrough lol).
> </div>

### Task 3 - More Scalable

Here is where it starts to get good. We learn more about cloudy things like `EC2` (servers running in the cloud aka running in AWS datacenters) and `Autoscaling`. We even get some foreshadowing on `containerization` and `serverless`. There is a very nice diagram.

> <div class="flag-toggle">🚩 Was EC2 Autoscaling the first autoscaling service in AWS? (yea/nay)</div>
> 
> <div class="flag-content">
> <code>Nay</code>
> </div>

> **SIDENOTE**
> In theory this was very easy for me to answer because one time at work I was in a trivia competition and one of the questions was `What was the first AWS service?` and I got it wrong in front of a bunch of my co-workers. So now, I will never forget that the the first AWS service was SQS. But in practice, I'm anal so I still googled it when I was walking through the THM room lol.

### Task 4 - More Reliable

Here we learn about the AWS global infrastructure, specifically `regions` and `availability` zones. You can learn all about these things [straight from the horse's mouth](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/), but here is the TLDR:

- **Regions**: is a physical location somewhere around the world - for example `us-east-1` is on the US east coast, and `eu-west-1` is in Ireland. Regions are made up of 1 or more Availability Zones. (This is straight from the AWS docs, but I have to say if there is really a region out there with only 1 availability zone that would be an extreme edge case.)
- **Availability Zones (AZs)** are one or more physical data centers (think those server rack pictures I linked to above). In AZs, data centers are distanced up to 60 miles apart from each other. The idea is - if there is a disaster - we want it to take down only one data center instead of the whole AZ.

You want to build and replicate your stuff across multiple AZs and, when possible, multiple regions.

> <div class="flag-toggle">🚩 How close together (in miles) should an Availability Zone's data centers be?</div>
> 
> <div class="flag-content">
> <code>60</code>
> </div>

I haven't watched the video in a while but I bet I also mention that `us-east-1` (Northern Virginia) is my comfort region. We all have one, and all the basic b**\*\*** like myself love `us-east-1`.

### Task 5 - More Reliable - Distributed Across the World (and in Space)

> <div class="flag-toggle">🚩 What continent has no AWS Region?</div>
> 
> <div class="flag-content">
> <code>Antarctica</code>
> </div>

> <div class="flag-toggle">🚩 What country has its own AWS partition?</div>
> 
> <div class="flag-content">
> <code>China</code>
> </div>

### Task 6 - Operational Expense vs Capital Expense

When I worked at AWS, we all had to give a presentation as part of onboarding that had it's own slide all about this - OPEX vs CAPEX is very important if you want to understand the business side of cloud (which I don't really 😉 - I just want to write lambda functions and event bridge rules all day - but we don't have a choice, understanding the business language is obviously critical).

- **Capital Expense (CAPEX)** - The old school way, a big up front investment in something you then own. For example, a building full of server racks.
- **Operational Expense (OPEX)** - Expenses incurred as part of your day-to-day operations - like your utilities (water + electricity). Generally pay-as-you-go.

> <div class="flag-toggle">🚩 Is a major purchase intended to be used by a business over a long period of time a capital expense or operating expense?</div>
> <div class="flag-content">
> <code>Capital expense</code>
> </div>

### Task 7 - API Mandate and the Two Pizza Team

Now I absolutely love that THM gave this topic it's own task because the more I work with AWS, the more I see the impact everywhere of the `Two Pizza Team` idea. AWS has hundreds of different `services`. You interact with all these different services via different APIs. Like a beautiful snowflake ❄️, no two AWS APIs are the same. And whilst you might yearn for all the AWS APIs to use a common language, they do not. And this is because within AWS, each service was/is built by different, small teams all given a lot of ownership over building their services like a unique product. Not so sure this is really how it is anymore, but that is how it was for a long time as all the AWS services were getting invented and built.

> **☁️NOTE**
> Also a lot of us who build on AWS like to complain about this because of the annoyance of having to figure out which APIs use `List` and which use `Describe`, but I don't want to come off as a hater. I think a lot of good has come out of the two pizza team ideology too.

> <div class="flag-toggle">🚩 Who announced the API mandate at AWS?</div>
> <div class="flag-content">
> <code>Jeff Bezos</code>
> </div>

### Task 8 - Free Open Source Capabilities

Here we start learning about different open source (OSS) tools important to the world of AWS.

Specifically, we learn about:

- `CloudFormation`
- `aws-data-wrangler`
- `aws-shell`
- `aws-lambda-powertools-python`

Of that list, I'm most familiar with `CloudFormation` and `aws-lambda-powertools-python`. In my video, I mostly bang on about CloudFormation, which I love and which has punished me more than any other.

> <div class="flag-toggle">🚩 What is AWS native "Infrastructure-as-Code" tool?</div>
> <div class="flag-content">
> <code>CloudFormation</code>
> </div>

### Task 9 - Serverless and Other Low-code Solutions

We learn about `serverless` and `low-code/no-code`.

- `serverless` - technologies for running code, managing data, and integrating applications, all without managing servers. AWS manages the compute power for you behind the scenes.
- `low-code/no-code` - tools that abstract away the actual writing of code by giving people things like drag-and-drop user interfaces. The example THM uses is **Honeycode** which is actually a dead AWS service (RIP 🪦) but used to be a tool non-developers could use to build simple apps by essentially writing spreadsheets - and AWS would turn those spreadsheets into working code behind the scenes. A better example nowadays might be something like **[Google Cloud AppSheet](https://cloud.google.com/appsheet?hl=en)**, although obviously that doesn't fit the AWS learning path.

> <div class="flag-toggle">🚩 Does serverless cost more or less when running idle than traditional servers?</div>
> <div class="flag-content">
> <code>`less`</code> The answer here is <code>less</code>, but actually this is so nuanced and debatable. Great question to have up your sleeve if you are at a tech conference and want to get everyone at the table talking so you don't have to say anything and can just slip away into your own thoughts. But the important and true thing (which is what they are teaching in the THM room) is that in a lot of use cases, serverless does save money, because you do not have to run a bunch of servers all the time and have them sit idle when nothing is happening. With serverless, you can just respond to traffic as it comes.
> </div>

### Task 10 - Summary

In the last task, you get hands on with a little website showing different rooms in the office. Click on each room in the office to talk to a different department and answer questions about cloud topics.

- DevOps (questions about latency and scalability)
- Software Engineering (questions about region naming and services)
- Finance (questions about expenses)
- CEO (final feasibility report)

**DevOps Questions**

> <div class="flag-toggle">🚩 The website will be accessible from all over the world - Shall we deploy all the infrastructure on our premises or go for cloud services?</div>
> <div class="flag-content">
> <code>cloud</code>
> </div>

> <div class="flag-toggle">🚩 What is the most practical reason for selecting the cloud services model?</div>
> <div class="flag-content">
> <code>Lesser latency rate for website users and easy scalability as the userbase grows.</code>
> </div>

**Software Engineering Questions**

> <div class="flag-toggle">🚩 The software engineering team mentioned that the complete team is housed in California (USA). Therefore they need a high-availability server in that region. In case AWS is selected as a cloud service provider, what would be the naming convention for that region?</div>
> <div class="flag-content">
> <code>us</code> (Find this in Task 4)
> </div>

> <div class="flag-toggle">🚩 Which of the following service will be used to route traffic based on users' geolocation?</div>
> <div class="flag-content">
> <code>Route 53</code> Not sure where in the task it says this, but I do know it's the answer.
> </div>

> <div class="flag-toggle">🚩 In line with Jeff Bezos's model at Amazon, each developer of our software team will expose the data to other members through a service interface called?</div>
> <div class="flag-content">
> <code>API</code> (Find this in Task 7)
> </div>

**Finance Question**

> <div class="flag-toggle">🚩 The payment will be made to cloud service providers on a pay-as-you-go model, and the infrastructure will be expanded per the needs. Which of the following expenses is optimally used in this case?</div>
> <div class="flag-content">
> <code>Optional</code> (Which I think is a bug and should be <code>Operational</code>? IDK I don't get that one) (Find this in Task 6)
> </div>

**CEO Final Boss Battle**

Here - you see a recap of your answers to the previous questions and then the final flag is revealed.

> <div class="flag-toggle">🚩 Final flag</div>
> <div class="flag-content">
> <code>Optional</code> 
> </div>
