Azure Storage

| Category | Description | Storage examples |
| --- | --- | --- |
| **Virtual machine data** | Virtual machine data storage includes disks and files. Disks are persistent block storage for Azure IaaS virtual machines. Files are fully managed file shares in the cloud. | Storage for virtual machine data is provided through Azure managed disks. Data disks are used by virtual machines to store data like database files, website static content, or custom application code. The number of data disks you can add depends on the virtual machine size. Each data disk has a maximum capacity of 32,767 GB. |
| **Unstructured data** | Unstructured data is the least organized. The format of unstructured data is referred to as *nonrelational*. | Unstructured data can be stored by using Azure Blob Storage and Azure Data Lake Storage. Blob Storage is a highly scalable, REST-based cloud object store. Azure Data Lake Storage is the Hadoop Distributed File System (HDFS) as a service. |
| **Structured data** | Structured data is stored in a relational format that has a shared schema. Structured data is often contained in a database table with rows, columns, and keys. Tables are an autoscaling NoSQL store. | Structured data can be stored by using Azure Table Storage, Azure Cosmos DB, and Azure SQL Database. Azure Cosmos DB is a globally distributed database service. Azure SQL Database is a fully managed database-as-a-service built on SQL. |

&nbsp;

ZRS zone dedundancy storage

&nbsp;

GRS redundancia geografica

RA-GRS (a de cima com leitura)

GZRS (zona + geo)

| Nó em um data center indisponível | Data center inteiro indisponível | Interrupção em toda a região | Acesso de leitura durante a interrupção em toda a região |
| --- | --- | --- | --- |
| \- **LRS**  <br>\- **ZRS**  <br>\- **GRS**  <br>\- **RA-GRS**  <br>\- **GZRS**  <br>\- **RA-GZRS** | \- **ZRS**  <br>\- **GRS**  <br>\- **RA-GRS**  <br>\- **GZRS**  <br>\- **RA-GZRS** | \- **GRS**  <br>\- **RA-GRS**  <br>\- **GZRS**  <br>\- **RA-GZRS** | \- **RA-GRS**  <br>\- **RA-GZRS** |