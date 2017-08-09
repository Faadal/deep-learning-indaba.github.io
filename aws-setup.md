---
layout: page
title: AWS Setup Instructions
permalink: /aws-setup/
---
# Amazon Web Services Setup Instructions

Amazon Web Services (AWS) is one of the world's largest cloud service providers. They allow users to run certain virtual machines (VMs) (and other services) in the cloud for free! 
We will use free VMs on AWS to run the practicals for the Indaba. We have created an "image" for your VMs with all the tools you need pre-installed to make this as easy as possible.
Follow this step-by-step guide to set your VMs set up in AWS! 

## Step 1: Create an Account and Sign-in
This first step is to create an Amazon account which will give you access to their free tier. As part of their identity verification policy, Amazon
usually requires you to provide the details of a *credit card*. Note that as long as you stay within the free tier, your credit card *will not be charged*. It is
only used for vertification purposes and you will only be billed if you exceed your free tier usage. If you follow this guide, you will not exceed this usage. 
We understand that some of you may not have personal credit cards and may not be able to borrow one from friends or family. If you can't get access to a 
credit card, please stop here, fill in [this form](https://goo.gl/forms/nRP1WJPSp1uShmkp2) and the head tutor will contact you with further instructions. 

### I have a credit card and don't have an AWS account
If you don't have an AWS account already, create one by going to the [AWS
homepage](http://aws.amazon.com/), and clicking on the yellow "Sign In to the
Console" button. It will direct you to a signup page which looks like the
following.

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-new-user.png'>
</div>

Select the "I am a new user" checkbox, click the "Sign in using our secure
server" button, and follow the subsequent pages to provide the required details.
They will ask for a credit card information, and also a phone verification, so
have your phone and credit card ready.

Proceed to the "I have an AWS Account" section below. 

### I have an AWS Account
Once you have signed up, go back to the [AWS homepage](http://aws.amazon.com),
click on "Sign In to the Console", and this time sign in using your username and
password.

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-signin.png'>
</div>

Once you have signed in, you will be greeted by a page like this:

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-home.png'>
</div>

Make sure that the region information on the top right is set to London.
If it is not, change it to EU(London) by selecting from the dropdown menu
there.

## Step 2: Launch the VM: 
(Note that this step requires your account to be "Verified" by
 Amazon. If you have just signed up, this may take up to 2 hrs, and you may not be able to launch instances
 until your account verification is complete.)

Next, click on the EC2 link (first link under the Compute category). You will go
to a dashboard page like this:

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-ec2.png'>
</div>

Click the blue "Launch Instance" button, and you will be redirected to a page
like the following:

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-ami.png'>
</div>

Click on the "Community AMIs" link in the left menu and then type "deep-learning-indaba-test-vm" in the search box. The AMI should come up in the box. Click on the blue "Select" button. 

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-community.png'>
</div>

You will now be taken to the "Choose an Instance Type" page, where you can select what type of machine you want to use to run your VM. Leave the default selection of "t2.micro" that has the green "free tier eligible" tag. 

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-instance-type.png'>
</div>

Click on the blue "Review and Launch" button which will take you to the review page: 

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-review.png'>
</div>

Click on the blue "Launch" button.

You will now be asked to create a "key-pair". This is used to access your Virtual Machine through the command line. You will not need to do this to run the Indaba practicals, but it might be useful later on and may be necessary to trouble shoot your VM if it is having issues. Therefore, we will choose "Create a new key pair" in the drop down menu. Give it any name you like, for example "indaba-vm" and then click "Download key pair". This will download a file to your machine which you should keep safely for future use. 

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-key-pair.png'>
</div>

Once you have downloaded the key pair, click on the blue "Launch Instance" button. 

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-launch-status.png'>
</div>

Amazon will now start your VM, this may take a few minutes.

## Step 3: Configure Security
Amazon locks down your new VM by default, which is good from a security perspective, but requires us to add some security rules to access the services we need. 

Click on the "Services" menu in the top left and click on "EC2" in the "Compute" section to go to the EC2 Dashboard from earlier. 

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-ec2.png'>
</div>

Under "Resources", click on the "Running Instances" link

You should now see your VM in the table (Note there are 2 instances in this screenshot, but you should only have 1 if you followed these instructions) 

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-running-instance.png'>
</div>

Scroll the table to the "security groups" column and click on the link that says "launch-wizard-1"

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-instances-security.png'>
</div>

Click on the tab that says "Inbound"

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-security-group.png'>
</div>

Now click on the "Edit" button to bring up the "Edit inbound rules" dialog. 

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-edit-rules.png'>
</div>

Click on the "Add Rule" button, under type choose "Custom TCP Rule", in "Port Range" enter "5555" (without the quotes) and in the "CIDR, IP or Security Group" box, enter "0.0.0.0/0" (again without the quotes). 

Repeat the above, this time using a "Port Range" value of "8888". The dialog should look like this:

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-add-rule.png'>
</div>

Click "OK" to return to the Security Group Page:

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-security-after.png'>
</div>

## Step 4: Connect to Jupyter Notebooks on your VM
Navigate back to the EC2 Running Instances page.

Note what your VM says under the "Status Check" column. If it says "Initializing", you will need a wait a bit longer for Amazon to finish creating and intializing your VM. If it has a green tick with the text "2/2 checks passed" then you are ready to connect! 

Click on the checkbox corresponding to your VM

You will see, near the bottom of the screen, some text saying "Public DNS: <SOMETHING>.eu-west-2.compute.amazonaws.com". This is the public address of your VM that you can use to connect to. Copy this to your clipboard (not the "Public DNS: " part!). 

<div class='fig figcenter fighighlight'>
  <img src='/assets/aws-instance-dns.png' width='60%'>
</div>

Now you can navigate in your browser to to http://**PASTE MY PUBLIC DNS**:5555. You should see a page saying "Refreshed Notebooks" - this means that the latest versions of the practicals are now on your VM! :) 

<div class='fig figcenter fighighlight'>
  <img src='/assets/vm-refresh.png' width='60%'>
</div>


To access Jupyer Notebooks, navigate to:

https://**PASTE MY PUBLIC DNS**:8888  (Note the httpS!) 

If it asks you for a password, enter "wits2017" without the quotes. You are now at the home page of the practicals! 

<div class='fig figcenter fighighlight'>
  <img src='/assets/jupyter-home.png' width='60%'>
</div>


# Troubleshooting

### I can't find the deep-learning-indaba AMI
Make sure that your AWS region is set to EU (London) as the image will only be visible in that region. 


