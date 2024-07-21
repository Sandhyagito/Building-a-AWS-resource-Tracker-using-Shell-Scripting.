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
![image](https://github.com/user-attachments/assets/778feaa0-6119-47cd-8d65-ba5f8132a58b)

![image](https://github.com/user-attachments/assets/6b23d616-5493-4a0d-b9de-a7dd553ceb92)

# Usage
Create the Script on Your EC2 Instance:

Connect to your EC2 instance and create the script file:

vi aws_resource_tracker.sh

Copy the script content into the "aws_resource_tracker.sh" file and save it.

# Set Up AWS CLI:

Ensure your AWS CLI is configured with the necessary permissions:

aws configure

$ aws configure
AWS Access Key ID [None]: YOUR_ACCESS_KEY_ID
AWS Secret Access Key [None]: YOUR_SECRET_ACCESS_KEY
Default region name [None]: The AWS region you want to use as the default for your AWS CLI commands (e.g., us-east-1, us-west-2).
Default output format [None]: The format in which you want the AWS CLI to return responses. Options include json, yaml, yaml-stream, text, and table.


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

The crontab will run the script every day at 8 PM, and the output will be appended to the resourcetracker file.
