
# AWS Cost Optimization Through Lambda Function

This project helps reduce AWS costs by automatically detecting and stopping underutilized resources using AWS Lambda. It enables smarter cloud management through scheduled automation.

## 🚀 Key Features

- 🔍 Detect idle EC2, RDS, and EBS resources
- ⏰ Schedule automatic stop/start of instances
- 📩 Notify via Amazon SNS
- 📊 Log activity in CloudWatch
- 🔐 Role-based access control with IAM

## 🧱 Architecture Overview

- **Lambda Function**: Runs Python code to perform optimization tasks
- **CloudWatch Events**: Triggers the function on schedule
- **IAM Role**: Grants least-privilege access to AWS resources
- **SNS Topic**: Sends alerts or reports
- **Optional**: S3 bucket for storing logs or reports

## 📝 File Structure

```
AWS_Cost_Optimization_Through_Lambda_Function/
├── lambda_function.py         # Main logic for cost optimization
├── iam_policy.json            # IAM policy with required permissions
├── cloudwatch_schedule.json   # Sample CloudWatch EventBridge rule
├── requirements.txt           # Dependencies (boto3)
└── README.md                  # Project documentation
```

## ⚙️ Setup Guide

1. **Create IAM Role**
   - Use the `iam_policy.json` to attach necessary permissions.

2. **Deploy Lambda**
   - Runtime: Python 3.9+
   - Upload `lambda_function.py` in AWS Lambda console
   - Attach the created IAM role

3. **Schedule with CloudWatch**
   - Use `cloudwatch_schedule.json` to create periodic triggers

4. **Test**
   - Run Lambda manually for first test or wait for scheduled trigger

5. **Monitor**
   - View logs in CloudWatch
   - Subscribe to the SNS topic for alerts

## ✅ Required Permissions

Ensure Lambda has access to:
- EC2 (Describe/Stop)
- RDS (Describe/Stop)
- EBS Volumes (Describe/Delete)
- SNS (Publish)
- CloudWatch Logs

## 📌 Best Practices

- Tag all AWS resources (for better filtering)
- Use environment variables for config
- Monitor monthly savings via Cost Explorer

---

**Disclaimer**: Test thoroughly before production use. Improper automation can lead to data loss or service disruption.
