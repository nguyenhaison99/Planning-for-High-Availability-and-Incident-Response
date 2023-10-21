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
More details about each asset:

- **EC2 Instances:** These are the main app servers. We have 3 of them, and they're copied to Region 2 for backup.

- **EKS Clusters:** These manage apps in containers. We have 2 of them, also copied to Region 2 for backup.

- **VPC (Multi-AZ IPs):** Networking setup with IPs in multiple zones for redundancy; duplicated in Region 2.

- **ALB (Load Balancer):** Distributes traffic to EC2 instances; copied to Region 2 for backup.

- **SQL Cluster (Primary):** Our main database with 2 nodes for redundancy, replicated to Region 2.

- **SQL Cluster (Secondary):** A replica of the main database, also replicated to Region 2.

## DR Plan
### Pre-Steps:
Steps to prepare in Region 2:

1. Set up similar AWS resources in Region 2.
2. Create VPC with IPs in Region 2.
3. Configure EKS clusters in Region 2.
4. Deploy EC2 instances and link to Region 2's setup.
5. Set up ALB in Region 2 for traffic distribution.
6. Configure SQL clusters in Region 2 and synchronize data.
7. Establish connections between VPCs in both regions.



## Steps:
To switch to Region 2:
1. Direct traffic to Region 2's ALB via DNS changes.
2. Adjust EKS clusters in Region 2 for increased traffic.
3. Deploy EC2 instances in Region 2 within the same group.
4. Promote Region 2's secondary SQL cluster as primary.
5. Redirect app traffic to the new primary SQL cluster.
6. Monitor and tweak Region 2's resources for performance.
7. Keep data synchronized between primary and secondary SQL clusters in both regions.
