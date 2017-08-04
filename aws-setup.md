---
layout: page
title: AWS Setup Instructions
permalink: /aws-setup/
---

Amazon Web Services (AWS) is one of the world's largest cloud service providers. They allow users to run certain virtual machines (VMs) (and other services) in the cloud for free! 
We will use free VMs on AWS to run the practicals for the Indaba. We have created an "image" for your VMs with all the tools you need pre-installed to make this as easy as possible.
Follow this step-by-step guide to set your VMs set up in AWS! 

## Step 1: Creating an Account and Sign-in
This first step is to create an Amazon account which will give you access to their free tier. As part of their identity verification policy, Amazon
usually requires you to provide the details of a *credit card*. Note that as long as you stay within the free tier, your credit card *will not be charged*. It is
only used for vertification purposes and you will only be billed if you exceed your free tier usage. If you follow this guide, you will not exceed this usage. 
We understand that some of you may not have personal credit cards and may not be able to borrow one from friends or family. If you can't get access to a 
credit card, please stop here, fill in your name and email address in on *this spreadsheet* and the head tutor will contact you with further instructions. 

### I have a credit card and don't have an AWS account
If you don't have an AWS account already, create one by going to the [AWS
homepage](http://aws.amazon.com/), and clicking on the yellow "Sign In to the
Console" button. It will direct you to a signup page which looks like the
following.

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-signup.png'>
</div>

Select the "I am a new user" checkbox, click the "Sign in using our secure
server" button, and follow the subsequent pages to provide the required details.
They will ask for a credit card information, and also a phone verification, so
have your phone and credit card ready.

Proceed to the "I have an AWS Account" section below. 

## I have an AWS Account
Once you have signed up, go back to the [AWS homepage](http://aws.amazon.com),
click on "Sign In to the Console", and this time sign in using your username and
password.

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-signin.png'>
</div>

Once you have signed in, you will be greeted by a page like this:

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-homepage.png'>
</div>

Make sure that the region information on the top right is set to London.
If it is not, change it to EU(London) by selecting from the dropdown menu
there.

## Step 2: 
(Note that this step requires your account to be "Verified" by
 Amazon. If you have just signed up, this may take up to 2 hrs, and you may not be able to launch instances
 until your account verification is complete.)

Next, click on the EC2 link (first link under the Compute category). You will go
to a dashboard page like this:

<div class='fig figcenter fighighlight'>
  <img src='/assets/ec2-dashboard.png'>
</div>

Click the blue "Launch Instance" button, and you will be redirected to a page
like the following:

<div class='fig figcenter fighighlight'>
  <img src='/assets/ami-selection.png'>
</div>
