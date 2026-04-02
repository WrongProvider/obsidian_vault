Bom exercicio:

https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/Instructions/Labs/LAB_07-Manage_Azure_Storage.html

Storage Security Strategies

![ac2bc8d5b36f68037a4b73a45f779a03.png](../_resources/ac2bc8d5b36f68037a4b73a45f779a03-1.png)

&nbsp;

Shared Access Signature (SAS)

[https://myaccount.blob.core.windows.net/?restype=service&comp=properties&sv=2015-04-05&ss=bf&st=2015-04-29T22%3A18%3A26Z&se=2015-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=F%6GRVAZ5Cdj2Pw4tgU7IlSTkWgn7bUkkAg8P6HESXwmfK](https://myaccount.blob.core.windows.net/?restype=service&comp=properties&sv=2015-04-05&ss=bf&st=2015-04-29T22%3A18%3A26Z&se=2015-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=F%256GRVAZ5Cdj2Pw4tgU7IlSTkWgn7bUkkAg8P6HESXwmf%4B)

&nbsp;

| Parameter | Example | Description |
| --- | --- | --- |
| **Resource URI** | `https://myaccount.`**`blob`**`.core.windows.net/` `?restype=`**`service`** `&amp;comp=properties` | Defines the Azure Storage endpoint and other parameters. This example defines an endpoint for Blob Storage and indicates that the SAS applies to service-level operations. When the URI is used with `GET`, the Storage properties are retrieved. When the URI is used with `SET`, the Storage properties are configured. |
| **Storage version** | **`sv`**`=2015-04-05` | For Azure Storage version 2012-02-12 and later, this parameter indicates the version to use. This example indicates that version 2015-04-05 (April 5, 2015) should be used. |
| **Storage service** | **`ss`**`=bf` | Specifies the Azure Storage to which the SAS applies. This example indicates that the SAS applies to Blob Storage and Azure Files. |
| **Start time** | **`st`**`=2015-04-29T22%3A18%3A26Z` | (Optional) Specifies the start time for the SAS in UTC time. This example sets the start time as April 29, 2015 22:18:26 UTC. If you want the SAS to be valid immediately, omit the start time. |
| **Expiry time** | **`se`**`=2015-04-30T02%3A23%3A26Z` | Specifies the expiration time for the SAS in UTC time. This example sets the expiry time as April 30, 2015 02:23:26 UTC. |
| **Resource** | **`sr`**`=b` | Specifies which resources are accessible via the SAS. This example specifies that the accessible resource is in Blob Storage. |
| **Permissions** | **`sp`**`=rw` | Lists the permissions to grant. This example grants access to read and write operations. |
| **IP range** | **`sip`**`=168.1.5.60-168.1.5.70` | Specifies a range of IP addresses from which a request is accepted. This example defines the IP address range 168.1.5.60 through 168.1.5.70. |
| **Protocol** | **`spr`**`=https` | Specifies the protocols from which Azure Storage accepts the SAS. This example indicates that only requests by using HTTPS are accepted. |
| **Signature** | **`sig`**`=F%6GRVAZ5Cdj2Pw4tgU7Il` `STkWgn7bUkkAg8P6HESXwmf%4B` | Specifies that access to the resource is authenticated by using a Hash-Based Message Authentication Code (HMAC) signature. The signature is computed with a key using the SHA256 algorithm, and encoded by using Base64 encoding. |

Tip

&nbsp;

az storage container policy create --name &lt;stored access policy identifier&gt; --container-name &lt;container name&gt; --start &lt;start time UTC datetime&gt; --expiry &lt;expiry time UTC datetime&gt; --permissions &lt;(a)dd, (c)reate, (d)elete, (l)ist, (r)ead, or (w)rite&gt; --account-key &lt;storage account key&gt; --account-name &lt;storage account name&gt;

&nbsp;

Access control:

| **Azure artifact** | **Shared Key (storage account key)** | **Shared access signature (SAS)** | **Microsoft Entra ID** | **On-premises Active Directory Domain Services** | **Anonymous public read access** |
| --- | --- | --- | --- | --- | --- |
| Azure Blobs | Supported | Supported | Supported | Not supported | Supported |
| Azure Files (SMB) | Supported | Not supported | Supported with Microsoft Entra Domain Services or Microsoft Entra Kerberos | Supported, credentials must be synced to Microsoft Entra ID | Not supported |
| Azure Files (REST) | Supported | Supported | Supported | Not supported | Not supported |
| Azure Queues | Supported | Supported | Supported | Not Supported | Not supported |
| Azure Tables | Supported | Supported | Supported | Not supported | Not supported |