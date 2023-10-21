# Infrastructure

## AWS Zones
Identify your zones here
- Region 1: us-east-2
- Region 2: us-west-1


## Servers and Clusters

### Table 1.1 Summary
| Asset                            | Purpose                   | Size       | Qty    | DR                                           |
|----------------------------------|---------------------------|------------|--------|----------------------------------------------|
| EC2 Instances (VMs)              | Application Servers       | t3.micro   | 3      | Deployed to DR, replicated                 |
| EKS Clusters                      | Kubernetes Clusters       |            | 2      | Deployed to DR, replicated                 |
| VPC with Multi-AZ IP Addresses    | Networking                |            | 1      | Created in multiple locations               |
| Application Load Balancer (ALB)  | Load Balancer             |            | 1 per region  | Deployed to DR, replicated           |
| SQL Cluster (Primary)            | Primary Database Cluster  |            | 2      | Replicated to DR in different zones        |
| SQL Cluster (Secondary)          | Secondary Database Cluster|            | 2      | Replicated to DR in different zones        |

### Descriptions
More detailed descriptions of each asset identified above:

- **EC2 Instances (VMs):** These instances host the application and are running in an auto-scaling group across multiple availability zones. They serve as the primary compute resources.

- **EKS Clusters:** These Kubernetes clusters manage containerized applications and services. They are distributed across multiple availability zones for high availability.

- **VPC with Multi-AZ IP Addresses:** The VPC is set up with IP addresses spanning multiple availability zones to ensure network redundancy and availability.

- **Application Load Balancer (ALB):** ALBs distribute incoming application traffic across multiple EC2 instances for load balancing and failover support.

- **SQL Cluster (Primary):** The primary SQL cluster hosts the main database. It is set up with two instance nodes in different availability zones for redundancy and failover support.

- **SQL Cluster (Secondary):** The secondary SQL cluster acts as a replica of the primary cluster. It also has two instance nodes in different availability zones for failover.

## DR Plan
### Pre-Steps:
List steps you would perform to setup the infrastructure in the other region. It doesn't have to be super detailed, but high-level should suffice.

## Steps:
You won't actually perform these steps, but write out what you would do to "fail-over" your application and database cluster to the other region. Think about all the pieces that were setup and how you would use those in the other region