# Azure Storage Account Replication 

   ### Storage Account 
       Four Important Storage Services
       Blob = Objects
       Files = File system
       Queue = Messages
       Table = NoSQL data 
       <img width="830" height="239" alt="image" src="https://github.com/user-attachments/assets/d83fe75e-7a31-42b6-9019-d0ded332b814" />

Blob = Binary Large Object
Blob Storage is designed primarily for unstructured data.
Blob Storage as storage for binary and text data
### Types of Blobs
         1. Block Blob : Used for most ordinary files.Most application file uploads use block blobs.
         2. Append Blob : Designed for data that is primarily appended to, such as logs. Append Blob
         3. Page Blob : Designed for random read/write operations and is associated with scenarios such as Azure VM disks.
                  Random read/write
### Blob Access Tiers 
      Azure Blob Storage provides access tiers to optimize cost based on how frequently data is accessed.
      Current online tiers include:
      Hot  : Used for frequently accessed data.
      Cool : Used for data accessed less frequently.
                      Monthly reports
                      Older documents
                       Backups
      Cold  : Used for data accessed even less frequently while remaining online.
    here is also:
     Archive : Used for very rarely accessed data.

   Easy interview question

Q: Where would you store frequently accessed product images? 
Hot Blob Storage
<img width="1171" height="301" alt="image" src="https://github.com/user-attachments/assets/d507c075-d9e9-4342-800d-0b15ae8f439c" />



Azure storage  provide redundancy for storage , data stored primary  storage if primary storage lost , what will happen 
that's why Azure provide the primary and secondary copy for storage 
<img width="846" height="391" alt="image" src="https://github.com/user-attachments/assets/cd127c6e-7544-48e7-9387-fe074ac5ca5a" />

Two types of replication
Synchronous replication : copy the data immediately  from primary copy to secondary copy 
ASynchronous replication : data will move in the form of batches regular time interval  


### Storage Redundancy
Azure Storage keeps multiple copies of data to protect against hardware failures, network/power outages, and larger failures.
 ##### LRS — Locally Redundant Storage
         Chennai Region 
         Zone 1          zone2    zone 3
    3 copies of data stored in Zone 1 with different rocks and different servers 
<img width="564" height="336" alt="image" src="https://github.com/user-attachments/assets/f06ee3af-7795-465a-8505-ceb2d3fdd353" />


Save from Server failure  and rack failure 

#### ZRS — Zone-Redundant Storage
          Chennai Region  will have 3 zones 
          Azure copy your data with different zones 
<img width="1057" height="358" alt="image" src="https://github.com/user-attachments/assets/058e5efa-becd-4da9-ab66-51f168ca9f8e" />


#### GRS — Geo-Redundant Storage
<img width="1119" height="414" alt="image" src="https://github.com/user-attachments/assets/632f0a61-a43d-43d1-a15b-6e67619d8403" />

total 6 copies -- 3 copies primary  , 3 copies are secondary 

#### GZRS — Geo-Redundant Storage

<img width="1136" height="396" alt="image" src="https://github.com/user-attachments/assets/99fe977b-b3cf-4e62-b91d-4adf18717380" />
