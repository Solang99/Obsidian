EBS volumes are network drivers with limited performance, if you need a high performance hardware disk you need to use EC2 instance store
EC2 Instance Store has:
	- Better I/O performance
	- lose their storage if they're stopped
	- Good for buffer/ cache/ scratch data / tmp content
	- Risk of data loss if hardware fails
	- Backups and replication are entrusted to dev