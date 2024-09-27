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
2. Select the **EC2 instance** you want to monitor.
3. Go to the **Monitoring** tab and check for existing CloudWatch monitoring.
4. If **detailed monitoring** is not enabled, click **Manage Detailed Monitoring** and select **Enable** (this comes with additional costs).
5. You can now see enhanced metrics like CPU, disk I/O, network traffic, etc., with a 1-minute interval.

### Advanced:
- You can set **CloudWatch Alarms** to trigger alerts (email, SMS, etc.) when thresholds for metrics like CPU utilization are breached.

---

## 2. Set Up AWS CloudTrail for Logging API Calls

### Steps:
1. **Log in to AWS Console**, navigate to **CloudTrail**.
2. Click **Create Trail** and enter a trail name.
3. Specify an **S3 bucket** where logs will be stored.
4. Enable **log file validation** to ensure log integrity.
5. Enable logging for all regions to track API calls made across all AWS services.
6. Click **Create**.

### Monitoring:
- You can use **AWS CloudWatch** to monitor CloudTrail logs for unusual activity or set up alerts based on specific API calls.

---

## 3. Setup and Enable VPC Flow Logs for Network Monitoring

### Steps:
1. Navigate to the **VPC Dashboard** in the AWS Console.
2. Select the **VPC** or network interface for which you want to create flow logs.
3. Click **Create Flow Log**.
4. Choose the **destination** (CloudWatch Logs or S3) where flow logs will be stored.
5. Select a **filter** for logging (e.g., All, Accept, Reject).
6. Click **Create** to enable logging.

### Monitoring:
- Use **CloudWatch Logs** or query logs in **Amazon Athena** for detailed network traffic monitoring.

---

## 4. Set Up CloudWatch Logs for Application Monitoring

### Steps:
1. **Install CloudWatch Logs Agent** on your EC2 instances (Linux or Windows).
2. Configure the agent to collect logs from specific files, directories, or system logs.
3. In the **CloudWatch Logs Console**, create a **log group** and associate your EC2 logs with it.
4. Customize log retention and monitoring settings for the group.

### Advanced:
- Use **CloudWatch Logs Insights** for advanced querying and analysis of application logs.

---

## 5. Setup and Monitor S3 Bucket Access Logs

### Steps:
1. Navigate to the **S3 Dashboard**, select the **S3 bucket** you want to monitor.
2. Under the **Properties** tab, enable **Server Access Logging**.
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

## Summary

These configurations ensure comprehensive monitoring and logging for your AWS resources, enhancing security, performance optimization, and troubleshooting capabilities across your cloud environment.
