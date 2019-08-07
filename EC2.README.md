## Amazon EC2

Amazon EC2 is a web service that provides resizable compute capacity in the cloud. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing us to quickly scale capacity, both up and down, as our computing requirements change.

EC2 Pricing Models

| _S. No._| _Type_ | _Description_ |
|---|---|---|
|1.| **OnDemand**| Allows us to pay a fixed rate by the hour <br/> (or by the second) with no commitment |
|2.| **Reserved**|  Provides us with a capacity reservation, and offer <br/> a significant discount on the hourly charge  for an <br/>instance. Contract Terms ate 1 Year and 3 Year Terms|
|3.| **Spot**| Enables us to bid whatever price we wantfor instance <br/>capacity, providing for even greated savings if our  <br/>applications have flexible start and end times |
|4.| **Dedicated Hosts**| Physical EC2 server dedicated for our use.Dedicated  <br/> Hosts can help us reduce costs by allowing us to use<br/> our existing server-bound software licenses |

On Demand pricing is useful for 
- Users that want the low cost and flexibility of Amazon EC2 without any up-front paymentor long term commitment
- Applications with short tem, spiky, or unpredicatb;e workloads that cannot be interrupted
- Applications being developed or tested on Amazon EC2 for the first time.

Reserved pricings is useful for:
- Applications with steady state or predicatble usage
- Applications that require reserved capacity
- Users able to make upfront payments to reduce their total computing costs even further.

Reserved Pricing types:
- **Standard Reserved Instances** - These offer upto 75% off on demand isntances. The more we pay up front and longer the contract, the greater the discount
- **Convertible Reserved Instances** - These offer up to 54% off on demand capability to change the attributes of the RI as long as  the exchange results in the creation of Reserved Instances or equal or greater value
- **Scheduled Reserved Instances** - These are available to launch within the time windows we reserve. This option allows us to match our capacity reservation to a predicatable recurring schedule that only requires a fraction of a day, a week, or a month

Spot pricing is useful for:
- Applications that have flexible start and end times
- Applications that are only feasible at very low compute prices
- Users with urgent computing needs for large amounts of additional capacity.

Dedicated Hosts priving is useful for
- Useful for regulatory requiremnets thar may not support multi-tenant virtualization
- Great for licensing which does not support multi-tenacy or cloud deployments
- can be purchased On-Demand (hourly)
- Can be purchased as Reservation for up to 70% off on the On-Demad price.

EC2 Instance Types

|Family|Speciality|Use Case|
|:---:|:---:|:---:|
|F1|Field Programmable Gate Array|Genomics reserach, financial analytics, real-<br/>time video processing, big data etc.|
|I3|High Speed Storage|NoSQL DBs, Data Warehousing etc|
|G3|Graphics Intensive|Video Encoding/ 3D Application Sreaming|
|H1|High Disk Throughput|MapReduce-based workloads, distributed file<br/>systems such as HDFS and MapR-FS|
|T3|Lowest Cost, General Purpose|Wed Servers/Small DBs|
|D2|Dense Storage|Fileservers/Data Warehousing/Hadoop|
|R5|Memory Optimized|Memory Intensive Apps/DBs|
|M5|General Purpose|Application Servers|
|C5|Compute Optimized|CPU Intensive Apps/DBs|
|P3|Graphics/General Purpose GPU|Machine Learning, Bit Coin Mining etc|
|X1|Memory Optimized|SAP Hana/Apache Sparl etc|
|Z1D|High compute capacity and a high<br/> memory footprint|Ideal for electronic design automation (EDA) <br/> and certain relational database workloads with <br/> high-percor licensing costs|
|A1|Arm-based workloads|Scale out workloads such as web servers|
|U-6tb1|Bare Metal|Bare metal capabilities that eliminate <br/> virtualization overhead|

EC2 Instance Types - Mnemonic (FIGHT DR MC PXZAU)
- F - For FPGA
- I - IOPS
- G - Graphics
- H - High Disk ThroughPut
- T - Cheap General Purpose (think T2 Micro)
- D - For Density
- R - For RAM
- M - Main Choice for General Purpose Apps
- C - For Compute
- P - Graphics (thins Pics)
- X - Extreme Memory
- Z - Extreme Memory and CPU
- A - Arm Based workloads
- U - Bare Metal