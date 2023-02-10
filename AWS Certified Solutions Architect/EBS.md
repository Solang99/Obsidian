
An EBS volume is a network drive that can be attached to instances when they run, it allows the instances to persist data. Can be mounted to one instance at a time and are bound to a specific AZ 

### EBS Snapshot
Make a backup of your EBS volume at a point in time, it's not necessary to detach volume to do snapshot. Can be used across AZ region.
Feature
- EBS Snapshot archive: Move a snapshot to an "archive tier" will be 75% cheaper
- Takes 24/72h for restoring archive
- Deleted archive will be in trash bin for 1 day (or 1 year)


### Amazon Machine Image (AMI)
AMI are a customization of an EC2 instance (an EC2 with custom packages, monitor software or other)
EC2 instance can be launched from:
- A public AMI (provided by aws)
- Our own AMI
- An AWS marketplace AMI (an AMI made by someone else)

### EBS volume types
EBS volumes come in 6 types:
	- gp2/gp3 (SSD): General purpose SSD volume that balances price and performance for a wide variety of workloads
	- io1/ io2(SSD): Highest-performance SSD volume for mission-critical low latency or high throughput workloads
	- st1 (HDD): Low cost HDD volume designed for frequently accessed, throughput-intensive workloads
	- sc1: Lowest cost HDD volume designed for less frequently accessed workloads
Only gp2/gp3 and io1/io2 can be used as boot volumes

![[Pasted image 20230207111915.png]]


### EBS Multi-Attach
Some EBS can be attached to multiple EC2 instance in the same AZ where each instance has full read & write permissions.
Use Case:
	- Higher application availability in clustered linux application
	- Application must manage current write op
![[Pasted image 20230207112025.png]]

### EBS Encryption
When create an encrypted EBS volume:
- Data at rest is encrypted inside the volume
- All the data in flight moving between the instance and the volume is encrypted
- All snapshots are encrypted
How to encrypt an unencrypted EBS volume:
1. Create an EBS snapshot volume
2. Encrypt EBS volume
3. Create new EBS volume from the snapshot
4. Now the original volume can be encrypted