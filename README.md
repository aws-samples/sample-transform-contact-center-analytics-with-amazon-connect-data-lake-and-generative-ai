# Transform Contact Center Analytics with Amazon Connect Data Lake and Generative AI

## Introduction

Organizations need the capability to perform advanced analytics on the contact center data and build custom reports for different business needs. With Amazon Connect analytics data lake, organizations easily access and analyze contact center performance metrics using their preferred BI tool. With the analytics data lake, records are de-duped and ready to query; eliminating the need to build and maintain complex data pipelines to perform extract, transform, and load (ETL) operations to access Amazon Connect data to get it ready for analytics and artificial intelligence (AI) workloads.

Organizations use the analytics data lake with Amazon Athena and Amazon QuickSight, or other BI tools, to create customized reports and dashboards leveraging Generative AI. This helps managers track important metrics for improving customer experience and operational efficiency. For example, by visualizing agent performance, managers identify the best performers for lost order calls and optimize routing profiles to staff queues with these agents, leading to desired business outcomes.

In this solution, learn how to use Amazon Connect Data Lake to build advance analytics dashboard with Amazon QuickSight and QuickSight Gen BI (Generative AI capability)

## Prerequisites
It is assumed that you understand the use of the services below and you have the following prerequisites:
1. Amazon Connect
2. Amazon QuickSight
3. Amazon Athena
4. AWS Resource Access Manager
5. AWS LakeFormation
6. AWS CloudFormation

## Contact Records dashboard overview

This dashboard provides an overview of Contact Stats, focusing on metrics such as the total number of contacts, average contact duration, agent and contact interaction time, and time spent in the queue. It includes visualizations of these metrics by day, offering insights into contact trends and agent performance. The dashboard also provides average values for callback attempts, hold time, and after-contact work, helping to monitor overall efficiency and identify areas for improvement in contact center operations.


![Properties](images/ctr-ds-1.png?raw=true)

This dashboard focuses on Contact Attributes Analysis, providing insights into contact statistics, average duration, agent interaction times, and various other metrics. It includes details on reasons for disconnects, contacts by endpoint address, and queue-specific metrics. The dashboard also breaks down contact attributes such as initiation method, attribute keys, and attribute values, helping you gain deeper insights into the interactions and behavior patterns of contact center agents and customers.

![Properties](images/ctr-ds-2.png?raw=true)

This dashboard is an Agent Contact Leaderboard that displays key performance metrics for agents, including the greatest and least number of contacts handled, time spent on after-contact work, and agent interaction duration. It highlights agents with the longest and shortest contact durations, highest and lowest number of callback attempts, and longest time on hold. This dashboard provides a comprehensive view of agent performance, helping identify top-performing agents and areas for improvement to optimize contact center efficiency and customer satisfaction.


![Properties](images/ctr-ds-3.png?raw=true)

## Contact Lens dashboard overview

The Contact Statistics from Contact Lens dashboard shows key metrics such as average customer sentiment, agent sentiment, conversation duration, agent talk speed, and talk duration. The dashboard includes visualizations that break down these metrics by day, providing insights into daily performance trends.

![Properties](images/cl-ds-1.png?raw=true)

This dashboard focuses on the Category Analysis of contact center interactions. It also categorizes contacts by assigned categories, endpoint addresses, and reasons for disconnects. The dashboard helps in understanding the distribution of contacts across different categories and provides detailed insights into agent and customer interactions, enabling better analysis and optimization of contact center performance.

![Properties](images/cl-ds-2.png?raw=true)

This dashboard is an Agent Contact Lens Leaderboard that displays various metrics to evaluate agent performance and customer interactions. It includes categories such as highest and lowest customer sentiment, highest and lowest agent sentiment, and longest and shortest conversation durations. Additional metrics, such as talk speed and talk duration, help analyze both agent and customer behaviors during interactions. The dashboard helps identify top and bottom-performing agents and provides insights to optimize agent training and overall contact center performance.

![Properties](images/cl-ds-3.png?raw=true)

## Generative AI usecase for Contact Center

You use Amazon QuickSight native Generative AI capabilities for your Contact Center with Amazon Connect data lake.

_Note: Generative AI technology delivers accurate responses when paired with effective prompt engineering. Use prompt engineering techniques to provide clear and precise instructions to enhance the quality and relevance of AI-generated responses. Well-crafted prompts lead to better context, improved output, and higher overall accuracy._

### Usecaes 1: Query caller information with natural language

The user has asked a natural language question: _"how many times caller with email address user12@mail.com called in last 24 hours"_ and the system has interpreted and analyzed this query.


![Properties](images/gen-1.png?raw=true)

### Usecaes 2: Build dashboard with natural query

When a user types a simple question like _"What is average agent interaction duration in mins,"_ the system automatically interprets it, identifies the relevant data source, and performs the necessary calculations. The results are then displayed in a clear, easy-to-read format, showing the average duration as 0.04 minutes. You can add this analysis to the QuickSightdashboard.


![Properties](images/gen-2.png?raw=true)

Users can modify the visualization by simply typing instructions. In this case, the user has requested to _"add green color where number of contacts is more than 200"_ - which explains why queue1 and queue3 are highlighted in green as they exceed the 200-contact threshold. This feature makes data visualization customization intuitive and accessible without requiring technical expertise in chart formatting or coding.

![Properties](images/gen-3.png?raw=true)

### Usecaes 3: Generate Contact Center executive summary

Users can simply prompt the system with instructions like _"Create a executive summary for contact center performance last week,"_ and the AI automatically analyzes multiple KPIs to create a comprehensive executive summary. The system intelligently combines these metrics, identifies trends, and presents them in a clear, business-focused narrative without requiring manual data compilation or advanced analytical skills.

![Properties](images/gen-4.png?raw=true)

### Usecaes 4: Build custom agent coaching plan

This image showcases QuickSight's "Data to insights" generative AI feature, which transforms complex agent performance analysis into automated coaching plans. The user has prompted the system to "Generate a personalized agent coaching plan by analyzing individual metrics against team benchmarks.." for a specific agent (exampleuser2). The AI analyzes multiple performance metrics, including after-contact work duration, total duration per contact, interaction times, sentiment scores, and total contact volume. The system automatically compares these metrics to team averages and provides a structured, step-by-step analysis. This demonstrates how the AI feature can quickly process multiple data points to create personalized performance insights and coaching recommendations, eliminating the need for manual data analysis and making performance management more efficient and data-driven.


![Properties](images/gen-5.png?raw=true)

## Architecture Overview

In this architecture, Amazon Connect make the data available to you through Amazon Athena. Once you configure the data sharing it creates a RAM invitation to the consumer account. RAM is a service to help you securely share resources across AWS accounts. AWS Lake Formation simplifies the creation, management, and governance of data lakes. By automating data ingestion, cataloging, security, and access control, it helps organizations efficiently manage large volumes of data for analytics, reporting, and machine learning purposes. Amazon Athena lets you analyze the data using standard SQL to run ad-hoc queries and get results. The data in Amazon Athena is visualed with Amazon QuickSignt.

![Properties](images/qs-dl-architecture.drawio.png?raw=true)

Fig - 1: Architecture diagram

## Solution Walkthrough


### Step 1: Create Amazon Connect instance and enable Amazon Connect Data Lake

1. Search Amazon Connect service
![Properties](images/1.png?raw=true)
2. Add an Amazon Connect Instance
![Properties](images/2.png?raw=true)
3. Enter a globally unique name to access your instance
![Properties](images/3.png?raw=true)
4. Enter admin user details
![Properties](images/4.png?raw=true)
5. Keep the default entires in the subsiquent screen and create the instance
6. Click on the Instnace Alias
![Properties](images/5.png?raw=true)
7. Click on Analytics tools
![Properties](images/6.png?raw=true)
8. Click on Add data share
![Properties](images/7.png?raw=true)
9. Copy the AWS account number
![Properties](images/8.png?raw=true)
10. Add data share
![Properties](images/9.png?raw=true)
11. Validate data share is successful
![Properties](images/10.png?raw=true)

### Step 2: Data Share configuration

1. Search for Resource Access Manager
![Properties](images/11.png?raw=true)
2. Navigate to Resource shares and select LakeFormation under pending status
![Properties](images/12.png?raw=true)
3. Accept the resource share
![Properties](images/13.png?raw=true)
4. Copy the Resource ID for glue:Catalog and glue:Database
![Properties](images/13.1.png?raw=true)
5. Search for AWS Lake Formation service
![Properties](images/14.png?raw=true)
6. In the pop up select "Add myself" and click Get started
![Properties](images/15.png?raw=true)

### Step 3: Setup Amazon QuickSight
1. Search for Amazon QuickSight service
![Properties](images/16.png?raw=true)
2. Click on Sign up for quicksight
![Properties](images/17.png?raw=true)
3. Enter the email address and unique account name and Finish. Keep all other configuration as it is
![Properties](images/18.png?raw=true)
4. Click on Go to Quicksight
![Properties](images/19.png?raw=true)
5. Open CloudShell, copy the aws account id. Update the below comman with your account ID and execute it in cloud shell 
__aws quicksight  list-users --aws-account-id "accountNumber" --namespace default__
![Properties](images/20.png?raw=true)
6. Copy the user part of the ARN. Example, "user/default/WSOpsRole/Op"

### Step 4 (CFT): Setup views with Amazon Athena


1. Download the datalake.yaml cloudformation from [here](https://github.com/aws-samples/sample-transform-contact-center-analytics-with-amazon-connect-data-lake-and-generative-ai/blob/main/datalake).
2. Search AWS CloudFormation service
![Properties](images/21.png?raw=true)
3. Click Create stack
![Properties](images/22.png?raw=true)
4. Upload the template and execute the stack
![Properties](images/23.png?raw=true)
5. Verify if the QuickSightRole is same as step 3.5. If not update "QuickSightRole" parameter. RAMDataLake must match glue:Database (step 2.4) and RAMOwner must match glue:Catalog (step 2.4)
![Properties](images/24.png?raw=true)
6. Once the stack executes, click on "Output" and copy the bucket name for "AthenaQueryS3QueryResultsOutput" key. Example, "datalake-795716566622-athena-results-s3"
![Properties](images/25.png?raw=true)
7. Search Amazon Athena Service
![Properties](images/26.png?raw=true)
8. Click on the Query Editor and click on Edit settings
![Properties](images/27.png?raw=true)
9. Add the s3 bucket you copied in step 4.6. Example "s3://datalake-795716566622-athena-results-s3"
![Properties](images/28.png?raw=true)
10. Click on all the hyper link value for the Keys under the template Outputs. This will execute the creation of views in Athena. This will be used by QuickSight
![Properties](images/25.png?raw=true)
11. Click Run for the 5 views
![Properties](images/29.png?raw=true)

### Step 5 (CFT): Setup up Contact Record dashboard

1. Download the CTR QuickSight dashboard CloudFormation template from [here](https://github.com/aws-samples/sample-transform-contact-center-analytics-with-amazon-connect-data-lake-and-generative-ai/blob/main/quicksight-contact-record).
2. Click on Create Stack, then "With new resources"
![Properties](images/30.png?raw=true)
3. Upload the CTR CFT downloaded in step 5.1
![Properties](images/31.png?raw=true)
4. Use the default parameter and click Run
![Properties](images/32.png?raw=true)
5. Acknowledge the steps and Submit
![Properties](images/33.png?raw=true)

### Step 6 (CFT):  Setup up Contact Lens dashboard

1. Download the CL QuickSight dashboard CloudFormation template from [here](https://github.com/aws-samples/sample-transform-contact-center-analytics-with-amazon-connect-data-lake-and-generative-ai/blob/main/quicksight-contact-lens).
2. Run the steps 5.2 through 5.5. Use the CL CFT downloaded in step 6.1

### Step 7: Setup dashboard access

1. Click on Manage QuickSight
![Properties](images/34.png?raw=true)
2. Click Manage Assets
![Properties](images/35.png?raw=true)
3. Click on Dashboard
![Properties](images/36.png?raw=true)
4. Select all the dashboards and click share.
![Properties](images/37.png?raw=true)
5. Enter the user i.e the email address you entered in step 3.3 and click share
![Properties](images/38.png?raw=true)
6. Confirm it's done
![Properties](images/39.png?raw=true)
7. Select all the other resources and share as necessary
![Properties](images/40.png?raw=true)

### Step 8: Access the dashboard

1. Go to dashboard (by clikcing on the top left Quicksight icon)
![Properties](images/41.png?raw=true)

### Step 9: Configure Amazon Q in QuickSight

Please follow the instructions [here](https://docs.aws.amazon.com/quicksight/latest/user/generative-bi-get-started.html) to enable and learn about Amazon Q in QuickSight.

## Validation

Turn on Contact Lens and place test calls/chat. Dashboard will show data

## Clean up

1. Delete CloudFormation template
2. Empty and delete the S3 bucket created while executing the CloudFormation template
3. Turn off Data Lake

## Conclusion

You have learnd how to configure Amazon Connect Data Lake and vizuale it's data in Amazon Quicksight




