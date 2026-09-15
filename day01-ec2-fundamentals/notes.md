# Day 1: EC2 Fundamentals

## Study Topics

### EC2 Basics
- **What is EC2?** Elastic Compute Cloud provides resizable compute capacity in the cloud
- **Key Benefits**: Scalability, flexibility, cost-effectiveness, integration with other AWS services
- **Use Cases**: Web servers, application servers, batch processing, development/test environments

### EC2 Instance Types
- **General Purpose**: T3, T3a, M5, M5a (balanced compute, memory, networking)
- **Compute Optimized**: C5, C5a, C6i (high-performance processors)
- **Memory Optimized**: R5, R5a, X1 (memory-intensive applications)
- **Storage Optimized**: I3, D3, H1 (high-speed local storage)
- **Accelerated Computing**: P3, G4, Inf1 (GPUs, FPGAs, specialized hardware)

### Amazon Machine Images (AMIs)
- **Definition**: Pre-configured templates for EC2 instances
- **Types**: 
  - Amazon Linux AMI (Amazon-maintained)
  - Ubuntu AMI (Community-maintained)
  - Windows AMI (Microsoft-maintained)
  - Custom AMIs (User-created)
- **Components**: Root device template, launch permissions, block device mapping

### Key Pairs
- **Purpose**: Secure SSH access to Linux instances
- **Components**: Public key (stored in AWS), Private key (downloaded by user)
- **Best Practices**: 
  - Download and secure private key immediately
  - Use different key pairs for different environments
  - Rotate keys regularly
  - Never share private keys

### Security Groups
- **Definition**: Virtual firewalls controlling inbound/outbound traffic
- **Characteristics**:
  - Stateful (return traffic automatically allowed)
  - Associated with network interfaces
  - Evaluated in order (most specific first)
  - Default: Allow all outbound, deny all inbound
- **Best Practices**:
  - Principle of least privilege
  - Use descriptive names and descriptions
  - Regularly audit and remove unused rules
  - Reference other security groups when possible

### Elastic IP Addresses
- **Purpose**: Static IPv4 address for dynamic cloud computing
- **Characteristics**:
  - Allocated to your AWS account
  - Can be associated/disassociated with instances
  - Remains associated until explicitly released
  - Charges apply when not associated with running instance
- **Use Cases**: 
  - Failover scenarios
  - DNS whitelisting
  - Remote access requiring static IP

### EC2 Instance Lifecycle
1. **Pending**: Instance is being prepared
2. **Running**: Instance is operational
3. **Stopping**: Instance is being stopped
4. **Stopped**: Instance is halted (EBS data preserved)
5. **Terminating**: Instance is being permanently deleted
6. **Terminated**: Instance is deleted (cannot be recovered)

### Stop vs Terminate
- **Stop**: 
  - Instance state saved to EBS volume
  - No compute charges (storage charges still apply)
  - Can be started again
  - Public/IP changes (unless Elastic IP used)
- **Terminate**:
  - Instance and attached EBS volumes deleted (unless deleteOnTermination=false)
  - Cannot be recovered
  - All resources released

### Monitoring Options
- **Basic Monitoring**: Free, 5-minute intervals
- **Detailed Monitoring**: Additional cost, 1-minute intervals
- **Enabling Detailed Monitoring**:
  - AWS Console: EC2 → Instances → Select instance → Actions → Monitoring → Enable detailed monitoring
  - AWS CLI: `aws ec2 monitor-instances --instance-ids i-xxxxxxxxxxxxxxxxx`
  - CloudWatch: View metrics at 1-minute granularity

## Key Concepts to Remember
- Instance types are optimized for different workloads
- AMIs define the software configuration
- Security groups act as instance-level firewalls
- Key pairs provide secure SSH access
- Elastic IPs provide static public IP addresses
- Understanding instance lifecycle is crucial for cost management
- Monitoring options affect granularity and cost

## References
- [Amazon EC2 Documentation](https://docs.aws.amazon.com/ec2/index.html)
- [EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/)
- [EC2 Pricing](https://aws.amazon.com/ec2/pricing/)