## Elastic IP
An Elastic IP (EIP) is a **static IPv4 address** designed for **dynamic cloud computing**. You can associate an EIP with your **instance** or **ENI** to allow **external internet access**.

## Key Features of Elastic IP:
Static: **Remains unchanged** unless manually released.
Reassignable: Can be **reassigned between instances** in your account.
One Free IP: **AWS provides one Elastic IP per account** without cost if it is associated with a **running instance**.

## Practical Steps to Assign an Elastic IP:
Go to the **EC2 Dashboard** in the **AWS Management Console**.
Select **Elastic IPs** from the left-hand menu.
Click **Allocate Elastic IP address**.
Associate the **EIP** with an **instance** or **network interface**.

## Placement Groups
AWS Placement Groups are **logical groupings of instances** that allow applications to meet specific **performance** or **redundancy** requirements.

## Types of Placement Groups:

## Cluster Placement Group:
Instances are placed **close together** within a **single Availability Zone**.
Provides **high throughput** and **low latency**.
Ideal for **HPC (High-Performance Computing)** and **big data workloads**.

## Spread Placement Group:
Instances are placed across **different hardware** within an **Availability Zone**.
Increases **fault tolerance**.
Ideal for **small critical workloads**.

## Partition Placement Group:
Instances are divided into **logical partitions**.
Each partition is **isolated** from others.
Used for **large distributed and replicated workloads** such as **HDFS, HBase, and Cassandra**.

Practical Steps to Create a Placement Group:
Open the **EC2 Dashboard** in the **AWS Management Console**.
Select **Placement Groups** from the left-hand menu.
Click **Create Placement Group** and provide a name.
Choose the **type of placement group** and add the instances during or after creation.

## NACL (Network Access Control List) vs Security Group

## NACL (Network Access Control List):
Acts as a **firewall** for controlling traffic **in and out of subnets**.
Operates at the **subnet level**.
**Stateless**: Rules must be defined for **both inbound and outbound traffic**.
Supports **Allow and Deny** rules.
Rules are evaluated by **rule number**.

## Security Group:
Acts as a **firewall** for controlling traffic **to and from an instance**.
Operates at the **instance level**.
**Stateful**: Automatically allows **return traffic**.
Supports **Allow rules only**.

Key Differences:

| Feature | NACL | Security Group |
|-------|------|----------------|
| Level | **Subnet-level** | **Instance-level** |
| Firewall Type | **Network-level firewall** | **Instance-level firewall** |
| State | **Stateless** | **Stateful** |
| Rule Actions | **Allow and Deny** | **Allow only** |
| Rule Order | **Rule number based** | **No rule order** |
| Inbound Rules | **Explicitly required** | **Explicitly required** |
| Outbound Rules | **Explicitly required** | **Automatically allowed** |
| Default Behavior | **Allows all traffic** | **Denies all traffic** |
| Scope | **Multiple subnets** | **Single instance** |

Key Takeaway:
**NACL = Subnet-level + Stateless + Allow/Deny**
**Security Group = Instance-level + Stateful + Allow only**

Practical Steps to Manage NACL:
Navigate to the **VPC Dashboard** in the **AWS Management Console**.
Select **Network ACLs** from the left-hand menu.
Create a **new NACL** and associate it with **subnets**.
Add **inbound and outbound rules** as required.

Practical Steps to Manage Security Groups:
Open the **EC2 Dashboard**.
Select **Security Groups** from the left-hand menu.
Create a **new security group** with **inbound and outbound rules**.
Attach the **security group** to instances during or after launch.
