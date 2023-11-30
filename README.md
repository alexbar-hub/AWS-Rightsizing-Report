# AWS-Rightsizing-Report
Generate Rightsizing Recommendation reportss on a schedule, save 2 CSVs in S3 and send SNS notification to teams.

- [AWS-Rightsizing-Report](#aws-rightsizing-report)
  - [Intro](#intro)
  - [What it does](#what-it-does)
  - [Deployment](#deployment)


## Intro
This project builds all you need in order to get a rightsizing report delivered directly to your mailbox and to your Slack channel on a schedule. The report contains 2 files (see below for details) and it also contains the AWS accounts name for better readability.

## What it does
This CloudFormation Stack creates the following resources:
* a lambda function to generate the reports;
* an S3 bucket to store the reports;
* an event rule to trigger the lambda function on a schedule;
* an SNS topic to deliver the notification

The report process:
* runs on the first Monday of each month;
* can be executed on-demand running the Lambda function;
* saves all generated outputs into the S3 bucket in the root account;
* delivers the notification via SNS to both email and https endpoints;
* generates 2 reports:
  * detailed report: contains all details plus the AWS account names for each finding;
  * summarized report: contains only the bare minimum info needed in order to action the recommendation
* creates pre-signed Urls to download the reports, the Urls have a validity of 12 hours;

## Deployment
In order to deploy this template:
* open CloudFormation in the billing account;
* populate all the required fields above;
* submit;

