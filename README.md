# Introduction-to-Amazon-Auto-Scaling


# AWS Auto Scaling Group Lab

## 🎯 Project Overview

This lab demonstrates how to create and configure an AWS Auto Scaling Group (ASG) with Launch Templates to automatically manage EC2 instance capacity. You'll learn how to set up self-healing infrastructure that maintains desired instance counts and automatically replaces failed instances.

## 🏗️ Architecture

The lab creates the following AWS infrastructure:

- **Default VPC**: Network environment with multiple availability zones
- **Launch Template**: Configuration blueprint for EC2 instances
- **Auto Scaling Group**: Manages 2 EC2 instances with automatic replacement
- **EC2 Instances**: Amazon Linux 2023 t2.micro instances

## 📋 Prerequisites

- AWS Account with appropriate permissions
- Basic understanding of EC2 and VPC concepts
- Familiarity with AWS Management Console

## 🛠️ Lab Tasks

### Task 1: AWS Console Access
- Signed in to AWS Management Console
- Set default region to **US East (N. Virginia) us-east-1**

### Task 2: Provision Default VPC
1. Navigate to VPC console
2. Delete existing default VPC if present
3. Recreate default VPC using Actions → Create default VPC

### Task 3: Create Launch Template
Configure the launch template with:
- **Name**: `whizlabsLT`
- **AMI**: Amazon Linux 2023 kernel-6.1
- **Instance Type**: t2.micro
- **Security Group**: Default VPC security group
- **Key Pair**: Not included in template
<img width="1897" height="675" alt="Screenshot 2025-11-01 152855" src="https://github.com/user-attachments/assets/eb198d4b-499d-46f1-b24a-7d8e9fa78808" />

### Task 4: Create Auto Scaling Group
Set up the ASG with:
- **Name**: `whiz-ASG`
- **Launch Template**: whizlabsLT
- **VPC**: Default VPC (all subnets)
- **Desired Capacity**: 2 instances
- **Minimum Capacity**: 2 instances
- **Maximum Capacity**: 2 instances
- **Tag**: Name = ASG-EC2
<img width="1897" height="808" alt="Screenshot 2025-11-01 154222" src="https://github.com/user-attachments/assets/6b556126-680c-44a7-a727-9dbe7a493444" />
<img width="1888" height="815" alt="Screenshot 2025-11-01 154250" src="https://github.com/user-attachments/assets/d2a117bd-6603-4cbf-baa0-e3518ac4be52" />

### Task 5: Test Auto Scaling
1. Stop one running EC2 instance
2. Observe automatic termination of stopped instance
3. Verify new instance launches to maintain desired capacity


## 🔍 Key Concepts

### Launch Templates
Launch Templates are the recommended method for defining EC2 instance configurations in Auto Scaling Groups. They provide:
- Versioning capability
- Reusability across multiple ASGs
- Centralized configuration management

### Auto Scaling Benefits
- **High Availability**: Automatically replaces unhealthy instances
- **Self-Healing**: Maintains desired instance count
- **Cost Optimization**: Runs only needed instances
- **Flexibility**: Easy to update configuration via template versions

## 📊 Validation

The lab includes automated validation to verify:
- Launch Template creation
- Auto Scaling Group configuration
- Instance count maintenance
- Self-healing functionality
<img width="1488" height="731" alt="Screenshot 2025-11-01 155316" src="https://github.com/user-attachments/assets/39e3a16b-c5c4-4132-930b-329c1492bc92" />

## 💡 Real-World Applications

Auto Scaling Groups are essential for:
- **Web Applications**: Handle traffic spikes automatically
- **Batch Processing**: Scale workers based on queue depth
- **Cost Management**: Scale down during low-demand periods
- **Fault Tolerance**: Replace failed instances without manual intervention

## 🔗 Integration Opportunities

Auto Scaling integrates with:
- **CloudWatch**: Metrics-based scaling policies
- **Elastic Load Balancing**: Distribute traffic across instances
- **SNS**: Notifications for scaling events
- **CloudFormation**: Infrastructure as Code deployment

## 📝 Important Notes

- Never edit the 12-digit Account ID in AWS Console
- Always verify region is set to us-east-1
- Instance replacement may take 1-2 minutes
- Default security group is used (customize for production)

## 🎓 Learning Outcomes

After completing this lab, I understand:
- How to create and configure Launch Templates
- Auto Scaling Group setup and configuration
- How ASGs maintain desired capacity
- Self-healing infrastructure concepts
- Basic AWS automation principles

## 🚀 Next Steps

To extend this lab:
1. Implement dynamic scaling policies based on CPU utilization
2. Add Application Load Balancer for traffic distribution
3. Configure CloudWatch alarms for scaling events
4. Create SNS notifications for instance state changes
5. Implement target tracking scaling policies

## 🔒 Security Considerations

For production environments:
- Create custom security groups with minimal required access
- Use specific IAM roles for EC2 instances
- Enable VPC Flow Logs for network monitoring
- Implement encryption for EBS volumes
- Use Systems Manager for secure instance access instead of key pairs

## 📚 Additional Resources

- [AWS Auto Scaling Documentation](https://docs.aws.amazon.com/autoscaling/)
- [Launch Templates Best Practices](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-launch-templates.html)
- [Auto Scaling Group Monitoring](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-monitoring-features.html)



---

**Lab Duration**: ~30 minutes  
**Difficulty Level**: Beginner  
**AWS Services Used**: EC2, VPC, Auto Scaling  
**Cost**: Minimal (within Free Tier for new accounts)
