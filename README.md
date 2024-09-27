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
