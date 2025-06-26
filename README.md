# Scalable Web Application with ALB and Auto Scaling

## Table of Contents
- [Solution Overview](#solution-overview)
- [Architecture Diagram](#architecture-diagram)
- [System Components](#system-components)
  - [DNS & External Access Layer](#dns--external-access-layer)
  - [Network Infrastructure Layer](#network-infrastructure-layer)
  - [Compute & Load Balancing Layer](#compute--load-balancing-layer)
  - [Data Persistence Layer](#data-persistence-layer)
  - [Monitoring & Alerting Layer](#monitoring--alerting-layer)
  - [Security & Access Control Layer](#security--access-control-layer)
- [Cost Optimization](#cost-optimization)

## Solution Overview

This project demonstrates how to deploy a secure, scalable, and highly available web application on AWS using EC2 instances. The architecture includes an Application Load Balancer (ALB) to distribute incoming traffic and an Auto Scaling Group (ASG) to automatically adjust the number of EC2 instances based on demand. For persistent storage, Amazon RDS is used as a managed relational database, deployed in Multi-AZ mode for high availability and data durability. The infrastructure spans multiple Availability Zones and follows AWS best practices for reliability, performance, and cost optimization.

## Architecture Diagram

![AWS_Architecture_Scalable_App (1)](https://github.com/user-attachments/assets/a872b98e-dab2-4a26-835c-c97fa0e47d94)
The diagram illustrates the infrastructure deployed across two Availability Zones with redundant components for high availability.

## System Components

### DNS & External Access Layer

**Amazon Route 53** provides DNS management, health checks, and traffic routing for the application.

### Network Infrastructure Layer

**VPC Configuration:**
- CIDR Block: 10.0.0.0/16
- Public Subnets: Host NAT Gateways and Load Balancer
- Private Subnets: Host EC2 instances and RDS
- NAT Gateways: Enable internet access for private resources
- Internet Gateway: Provides internet connectivity

### Compute & Load Balancing Layer

**Application Load Balancer (ALB):**
- Layer 7 load balancing
- SSL/TLS termination
- Health checks for targets
- Multi-AZ distribution

**Auto Scaling Group:**
- Manages 2 EC2 instances across different Availability Zones
- Dynamic scaling based on CloudWatch metrics
- Automatic instance replacement
- Multi-AZ deployment
- Integration with ALB

### Data Persistence Layer

**Amazon RDS:**
- Multi-AZ deployment for high availability
- Automated backups and point-in-time recovery
- Encryption at rest and in transit
- Performance monitoring

### Monitoring & Alerting Layer

**Amazon CloudWatch:**
- Metrics collection for EC2, RDS, and ALB
- Custom dashboards and alarms
- Log aggregation

**Amazon SNS:**
- Email and SMS notifications
- Integration with CloudWatch alarms

### Security & Access Control Layer

**IAM Role:**
- Provides secure access permissions for EC2 instances
- Allows instances to interact with AWS services
- Eliminates need for hardcoded credentials
- Follows principle of least privilege

## Cost Optimization

This architecture implements several cost optimization strategies:

**Auto Scaling Benefits:**
- Automatically scales down during low traffic periods
- Eliminates over-provisioning of resources
- Pay only for resources actually needed

**Multi-AZ Efficiency:**
- Optimizes resource distribution across availability zones
- Reduces data transfer costs between zones
- Maintains availability while minimizing redundancy costs

**Load Balancer Optimization:**
- Application Load Balancer provides cost-effective Layer 7 routing
- Health checks prevent traffic routing to unhealthy instances
- Reduces wasted compute resources

**RDS Cost Management:**
- Multi-AZ deployment balances cost with availability requirements
- Automated backups reduce manual administrative overhead
- Performance monitoring helps right-size database resources

**Monitoring Efficiency:**
- CloudWatch provides granular resource monitoring
- Enables data-driven scaling decisions
- SNS alerts prevent costly downtime incidents
