Blob storage

&nbsp;

&nbsp;

| Comparison | Hot access tier | Cool access tier | Cold access tier | Archive access tier |
| --- | --- | --- | --- | --- |
| **Availability** | 99.9% | 99% | 99% | 99% |
| **Availability (RA-GRS reads)** | 99.99% | 99.9% | 99.9% | 99.9% |
| **Latency (time to first byte)** | milliseconds | milliseconds | milliseconds | hours |
| **Minimum storage duration** | N/A | 30 days | 90 days | 180 days |

&nbsp;

somente o General purpose v2 pode ter lifecycle

&nbsp;

block blobs -> default

append blobs -> data (bom para logging)

page blobs -> pode ter até 8Tb bom para read/write

&nbsp;

azcopy

azure data box disk

https://azure.microsoft.com/en-us/pricing/calculator/

&nbsp;

exsite uma coisa chamada sincronização de arquivos, isso faz um cache em um servidor fisico para syncronizar com arquivos em uma share do Azure.