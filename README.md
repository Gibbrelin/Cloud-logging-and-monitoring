# AWS Cloud Monitoring and Logging Setup Guide

This README provides step-by-step instructions to set up and enable AWS CloudWatch monitoring and other logging tools for monitoring and managing AWS resources like EC2, VPCs, S3, and RDS.

TABLE OF CONTENT:
1. Setup and Enable CloudWatch Monitoring for EC2 Instances 
2. Set Up AWS CloudTrail for Logging API Calls
3. Setup and Enable VPC Flow Logs for Network Monitoring
4. Set Up CloudWatch Logs for Application Monitoring
5. Setup and Monitor S3 Bucket Access Logs
6. Setup and Monitor RDS Database Metrics with CloudWatch
---

## 1. Setup and Enable CloudWatch Monitoring for EC2 Instances

### Steps:
1. **Log in to AWS Console** and navigate to the **EC2 Dashboard**.

![Screenshot 2024-09-27 142630](https://github.com/user-attachments/assets/b4028db3-205a-4e68-b32e-39937c4d4c89)

2. Go to instances on the left hand side and Select the **EC2 instance** you want to monitor.

![Screenshot 2024-09-27 142403](https://github.com/user-attachments/assets/93394971-88da-460e-9fd1-f942a148da6b)

3. Go to the **Monitoring** tab and check for existing CloudWatch monitoring.

![Screenshot 2024-09-27 143131](https://github.com/user-attachments/assets/9574c8d0-3afa-4a0b-8e47-a6f3339c1692)

4. If **detailed monitoring** is not enabled, click **Manage Detailed Monitoring** and select **Enable** (this comes with additional costs).

![Screenshot 2024-09-27 142434](https://github.com/user-attachments/assets/6e4d8707-fecc-488c-aa7c-cbc067116398)

5. You can now see enhanced metrics like CPU, disk I/O, network traffic, etc., with a 1-minute interval.

![Screenshot 2024-09-27 143622](https://github.com/user-attachments/assets/dab5fe55-f458-4ed5-93e0-540e9d7d0886)

### Advanced:
- You can set **CloudWatch Alarms** to trigger alerts (email, SMS, etc.) when thresholds for metrics like CPU utilization are breached.

---

## 2. Set Up AWS CloudTrail for Logging API Calls
AWS CloudTrail is a service that enables governance, compliance, and operational and risk auditing of your AWS account. It records AWS API calls for your account and delivers log files to an Amazon S3 bucket. The API call history captured by CloudTrail includes details such as the identity of the API caller, the time of the API call, the source IP address of the caller, and the request parameters.

### Steps:
1. **Log in to AWS Console**, navigate to **CloudTrail**.

![Screenshot 2024-09-27 144358](https://github.com/user-attachments/assets/38f9c56f-57a6-4b4e-8c34-7b4092c3965f)

2. Click **Create Trail** and enter a trail name.

![Screenshot 2024-09-25 160905](https://github.com/user-attachments/assets/0bf0d04c-ec49-4371-b8de-b846232ac2cd)

3. Specify an **S3 bucket** where logs will be stored.

![Screenshot 2024-09-25 161010](https://github.com/user-attachments/assets/8b2dde5d-0e29-4db9-818c-dc90441bad19)

4. Enable **log file validation** to ensure log integrity.

![Screenshot 2024-09-25 161138](https://github.com/user-attachments/assets/d967d3e7-89d4-418c-bfaf-79f82afe903c)

5. Enable logging for all regions to track API calls made across all AWS services.

![Screenshot 2024-09-25 161722](https://github.com/user-attachments/assets/b15380ab-f9fd-473f-9c88-6200682e8c38)

6.Review and Click **Create**.

![Screenshot 2024-09-25 161904](https://github.com/user-attachments/assets/51dd1ece-0374-4f44-9901-0dae68327865)

![Screenshot 2024-09-25 162114](https://github.com/user-attachments/assets/e631fa63-0b19-4d1a-b5ca-7b7dc5b4f29c)

### Monitoring:
- You can use **AWS CloudWatch** to monitor CloudTrail logs for unusual activity or set up alerts based on specific API calls.

---

## 3. Setup and Enable VPC Flow Logs for Network Monitoring

### Steps:
1. Navigate to the **VPC Dashboard** in the AWS Console.

![Screenshot 2024-09-25 162732](https://github.com/user-attachments/assets/17f2e934-bea2-4927-bcc8-788ae898a6e3)

2. Click on **VPC** and Select the **VPC** or network interface for which you want to create flow logs.

![Screenshot 2024-09-25 162837](https://github.com/user-attachments/assets/5d481573-0671-4bed-9dd3-49713b6bfaea)

3. Navigate to **Flow log** and Click **Create Flow Log**.

![Screenshot 2024-09-25 162951](https://github.com/user-attachments/assets/f139c09c-3130-4345-be24-516467875b8f)
![Screenshot 2024-09-25 163158](https://github.com/user-attachments/assets/c659c70b-5775-406a-ae31-c9f53a9a906d)

4. Select a **filter** for logging (e.g., All, Accept, Reject).

 ![Screenshot 2024-09-25 163243](https://github.com/user-attachments/assets/88f2a81a-70b6-4f66-8d9d-9927d4ce2df6)

5.  Choose the **destination** (CloudWatch Logs or S3) where flow logs will be stored.

![Screenshot 2024-09-25 163530](https://github.com/user-attachments/assets/d24453bb-9a99-40ad-ac2e-d07c5a2f25c0)

6. Click **Create** to enable logging.

### Monitoring:
- Use **CloudWatch Logs** or query logs in **Amazon Athena** for detailed network traffic monitoring.

---

## 4. Set Up CloudWatch Logs for Application Monitoring
Amazon CloudWatch Logs is a monitoring service that helps you collect, access, and analyze log data from your applications and services. By setting up CloudWatch Logs, you can monitor application health, troubleshoot issues, and optimize performance. This guide walks you through the steps of setting up CloudWatch Logs for application monitoring.

### Steps:

### Step 1: Create a Log Group
A **log group** is a container for log streams (individual logs from different sources).

1. In the **CloudWatch** dashboard, navigate to **Logs** from the left-hand menu.

![Screenshot 2024-09-25 164017](https://github.com/user-attachments/assets/c4102be9-68af-4b3d-982c-1bb28c9de350)

2. Click on **Log groups**.

3. Click **Create log group**.

![Screenshot 2024-09-25 164039](https://github.com/user-attachments/assets/1025fd6e-c970-46fe-9dda-f040e0506577)

4. Enter a **Log group name** (e.g., `/my-application/logs`).

![Screenshot 2024-09-25 164113](https://github.com/user-attachments/assets/f6833118-a075-4afb-9316-a99f4a7c103c)

5. (Optional) Set **Retention settings** to specify how long to keep the logs (e.g., 7 days, 30 days).

6. Click **Create log group**.

![Screenshot 2024-09-25 164131](https://github.com/user-attachments/assets/5f556241-6e34-40a5-8e52-7aee2f52ac35)


### Step 2: Set Up the Application to Send Logs to CloudWatch
To send your application's logs to CloudWatch, you need to configure the application's environment to push logs to CloudWatch Logs. This can be done through AWS services like **Amazon EC2**, **ECS**, **Lambda**, or by using the **CloudWatch Agent** (for this illustration we'll be using ec2 instance)

#### Configure CloudWatch Agent for EC2 or On-Premises Servers
1. **Install the CloudWatch Agent**:
   - For Linux, run:
     ```bash
     sudo yum install amazon-cloudwatch-agent
     ```
![Screenshot 2024-09-25 164513](https://github.com/user-attachments/assets/12099891-fec1-4a92-a529-1903e578d8e6)

   - For Windows, download and install the agent from the AWS documentation.
   
1. **Create a Configuration File**:
   - Use the CloudWatch Agent Wizard to create a configuration file:
     ```bash
     sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
     ```
   - The wizard will guide you through specifying the log file locations, log group names, and log stream names.

![Screenshot 2024-09-25 165341](https://github.com/user-attachments/assets/4746b48c-75bd-4904-a051-7482a0799ffe)

2. **Start the CloudWatch Agent**:
   - After creating the configuration file, start the agent:
     ```bash
     sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
     -a start \
     -c file:/path/to/config.json \
     -s
     ```
   
### Advanced:
- Use **CloudWatch Logs Insights** for advanced querying and analysis of application logs.

---

## 5. Setup and Monitor S3 Bucket Access Logs

### Steps:
1. Navigate to the **S3 Dashboard**, select the **S3 bucket** you want to monitor.

![Screenshot 2024-09-26 171748](https://github.com/user-attachments/assets/3f6c4752-afdd-4ad0-a9cb-7e0a50e3fb35)

2. Under the **Properties** tab,Go to  **Server Access Logging** click on edit and enable **Server Access Logging**.

![Screenshot 2024-09-26 171903](https://github.com/user-attachments/assets/459c06f9-fe67-44a5-8c71-e8c0a39d5883)
![Screenshot 2024-09-26 171933](https://github.com/user-attachments/assets/d7c16551-ff3e-4a3c-8a5b-c4eb19685dd3)


3. Choose a **target bucket** to store logs (can be the same bucket or a separate one).



4. Update the target bucket’s policy to allow S3 to write logs to it.

### Monitoring:
- Use **CloudWatch Logs** or tools like **AWS Athena** to analyze access logs for suspicious activity.

---

## 6. Setup and Monitor RDS Database Metrics with CloudWatch

### Steps:
1. In the **RDS Console**, select the **RDS instance** you want to monitor.
2. Go to the **Monitoring** tab and enable **Enhanced Monitoring** for more granular metrics (additional costs may apply).
3. View metrics such as CPU utilization, disk I/O, and memory usage under the **CloudWatch Metrics** section.

### Advanced:
- Set **CloudWatch Alarms** for critical database metrics like CPU utilization, read/write latency, or free storage space.

---
## Best practices for cloud monitoring and logging:

1. **Enable Multi-Layered Monitoring**: Use a combination of metrics, logs, and alerts to get a comprehensive view of system performance, security, and availability.
   
2. **Centralize Logs**: Aggregate logs from different services and applications into a centralized platform like AWS CloudWatch, ELK stack, or a third-party service for easier analysis.

3. **Set Up Automated Alerts**: Configure alerts for key metrics and anomalies to quickly respond to potential issues in real-time.

4. **Monitor Resource Usage**: Regularly track usage and costs to identify inefficient resource utilization and optimize cloud expenses.

5. **Implement Log Retention Policies**: Define appropriate retention periods for logs based on compliance and business needs to manage storage costs effectively.

6. **Use IAM and Secure Access**: Control who has access to monitoring tools and logs using AWS IAM policies or other identity management services to ensure only authorized users can access sensitive data.

By following these best practices, organizations can maintain high visibility into their cloud environment, enhance security, and ensure efficient operation.
## Summary

These configurations ensure comprehensive monitoring and logging for your AWS resources, enhancing security, performance optimization, and troubleshooting capabilities across your cloud environment.
