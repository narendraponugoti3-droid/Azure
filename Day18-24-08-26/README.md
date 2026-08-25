# File server Storage 


Storage Account --> File share Option --> then mount it 

Two types of file shares 
1. NFS : network file system --> Linux --> Host based --> work on port no 2049 
2. SMB - Server message block for windows -->entraid/username and passowrd -->445

Windows mechaine lo data mount to linux 
Linux machines --> install plugin samba inside linux machine 
Windows machine--> install plugin NFS client -- then mount the data from linux machine to windows 

1. Vent 10.0.0.0/16 with subnet 10.0.1.0/24
2. Create a Storage Account in Subnet
3. Inside Storage Account , we can create NFS and SMB
4. Then Create ONE Linux VM and One Windows machine and attach to NFS and SMB
5. Private endpoint --NIC and path of NFS :10.0.1.7/nfs


## Create the above requirments in AZURE 

1. Create VN with subnet 
2. Create linux VM and windows VM
3. Create a Storage Account 
