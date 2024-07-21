# Building-a-AWS-resource-Tracker-using-Shell-Scripting.
The AWS Resource Tracker is a bash script designed to report on various AWS resources including S3 buckets, EC2 instances, Lambda functions, and IAM users. This script provides a simple and efficient way to keep track of your AWS resource usage.

# Overview
The AWS Resource Tracker is a bash script designed to report on various AWS resources including S3 buckets, EC2 instances, Lambda functions, and IAM users. This script provides a simple and efficient way to keep track of your AWS resource usage.

# Features
List all S3 buckets
List all EC2 instances with their instance IDs
List all Lambda functions
List all IAM users

# Prerequisites
Before using this script, ensure you have the following:

AWS CLI is installed and configured on your machine.
**jq** installed for processing JSON outputs.
Sufficient AWS permissions to list resources.

# Script Content
#!/bin/bash

#######################
# Author: Sandhya
# Date: 21/07/2024
# Version: v1
# This script will report the AWS resource usage
########################

#set -x # debug mode

# AWS S3
# AWS EC2
# AWS Lambda
# AWS IAM Users

# list s3 buckets
echo "Print list of s3 buckets"
aws s3 ls >> resourcetracker

# list EC2 Instances
echo "Print list of ec2 instances"
aws ec2 describe-instances | jq '.Reservations[].Instances[].InstanceId' >> resourcetracker

# list Lambda functions
echo "Print list of lambda functions"
aws lambda list-functions >> resourcetracker

# list IAM users
echo "Print list of IAM users"
aws iam list-users >> resourcetracker

# Usage
Create the Script on Your EC2 Instance:

Connect to your EC2 instance and create the script file:

vi aws_resource_tracker.sh

Copy the script content into the "aws_resource_tracker.sh" file and save it.

# Set Up AWS CLI:

Ensure your AWS CLI is configured with the necessary permissions:

aws configure

Install jq:

If you don't have jq installed, you can install it using:

sudo yum install jq  # For Amazon Linux
sudo apt-get install jq  # For Ubuntu

# Run the Script:

Make the script executable and run it:

chmod +x aws_resource_tracker.sh # To add execute permissions for the file
./aws_resource_tracker.sh # command to run the script

# Check the Output:

The output of the script will be saved in the resourcetracker file in the current directory.

# Automating with Cron Job
To automate the execution of this script, you can set up a cron job to run it at a specified time.

Open the crontab configuration:

crontab -e
Add the following line to the crontab file to run the script every day at 8:00 PM:

0 20 * * * /path/to/aws_resource_tracker.sh
Replace /path/to/aws_resource_tracker.sh with the actual path to your script.

Save and exit the crontab editor.

![image](https://github.com/user-attachments/assets/0874dc45-c201-4f71-9129-e7b08cf999e0)

