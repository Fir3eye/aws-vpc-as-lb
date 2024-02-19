# 🥏AWS Project: Applications in Private Subnet Showcase
## ⛳Output
![image](https://github.com/Fir3eye/aws-vpc-as-lb/assets/93431222/541a5080-d1ce-4f33-8972-3efddd09b06a)



This AWS project demonstrates the setup of applications running in a private subnet using various AWS services. The infrastructure includes a Virtual Private Cloud (VPC), Launch Template, Autoscaling Group, Bastion Host, and Load Balancer.

## 🎢Steps of Creation

### 1. Create VPC

- Open the AWS Management Console.
- Navigate to the VPC service.
- Create a new VPC with private and public subnets.

### 2. Launch Template

- Create an EC2 Launch Template specifying the instance type, AMI, and other configurations.
  
### 3. Autoscaling Group

- Set up an Autoscaling Group using the Launch Template.
- Define scaling policies based on conditions like CPU utilization or network traffic.

### 4. Bastion Host

- Launch a public EC2 instance as a Bastion Host in the public subnet.
- Configure security groups to allow SSH access only from your IP address.

### 5. Copy Public Key to Bastion Host

- Copy your public key to the Bastion Host to enable secure access.
  
### 6. SCP Key to Private EC2 Instance

- Use SCP to copy the private key from your local machine to the private EC2 instance in the private subnet.
  
```bash
scp -i /path/key.pem /path/key.pem ubuntu@privateIP:/home/ubuntu


```

### 7. Run Demo App using Python3

- Connect to the private EC2 instance via the Bastion Host:

```bash
ssh -i /path/key.pem -o "ProxyJump ubuntu@bastionIP" ubuntu@privateIP
```


### 8. Target Group

- Create a Target Group for your private EC2 instances:

  - Navigate to "Target Groups" in the AWS EC2 service.
  - Create a new Target Group with health check settings.
  - Register your private EC2 instances in the Target Group.

### 9. Load Balancer

- Set up an Application Load Balancer (ALB):

  - Navigate to "Load Balancers" in the AWS EC2 service.
  - Create a new Application Load Balancer (ALB) with listeners and security settings.
  - Associate the ALB with the Target Group created in step 8.

- Test the load balancer:

  - Access your application through the ALB DNS. Traffic will be distributed among registered instances.


Feel free to customize and extend this project based on your specific application requirements.


