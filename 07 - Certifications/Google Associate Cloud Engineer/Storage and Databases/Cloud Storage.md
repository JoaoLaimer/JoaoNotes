Cloud Storage is Google Cloud’s object storage service, and it allows world-wide storage and retrieval of any amount of data at any time.
**Use Cases**:
- Website Content
- Storing data for archiving and disaster recovery
- Distributing large data objects to users via direct download
**Key Features**:
- Scalable to exabytes
- Time to first byte in milliseconds
- Very high availability across all storage classes
- Single API across storage classes


|                              | Standard                                                                               | Nearline                                                                                        | Coldline                                                                  | Archive                                              |
| ---------------------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ---------------------------------------------------- |
| **Use Case**                 | "Hot" data and/or sotred for only brief periods of time like data-intesive computation | Infrenquently accessed data like data backup, long-rail multimedia content, and data archiving. | Infrequently accessed data that you read or modify at most once a quarter | Data archiving, online backup, and disaster recovery |
| **Minimum storage duration** | None                                                                                   | 30 days                                                                                         | 90 days                                                                   | 365 days                                             |
| **Retrieval Cost**           | None                                                                                   | $0.01 per GB                                                                                    | $0.02 per GB                                                              | %0.05 per GB                                         |
| **Availability SLA**         | 99.95% (multi/dual)<br>99.90% (region)                                                 | 99.90% (multi/dual)<br>99.00% (region)                                                          | 99.90% (multi/dual)<br>99.00% (region)                                    | None                                                 |
| **Durabilitiy**              | All 99.999999999%                                                                      |                                                                                                 |                                                                           |                                                      |

**Buckets**
- Naming requirements
- Cannot be nested
**Objects**
- Inherit storage class of bucket when created
- No minimum size; unlimited storage
**Access**
- gcloud storage command
- (RESTful) JSON API or XML API

## Changing default storage classes
- Default class is applied to new objects
- Regional bucket can never be changed to Multi-Region/Dual-Region
- Multi-Regional bucket can never be changed to Regional
- Objects can be moved from bucket to bucket
- Object Lifecycle Management can manage the classes of objects
## Signed URLs
- "Valet Key" access to buckets and objects via ticket:
	- Ticket is a cryptographically signed URL.
	- Time-Limited
	- Operations specified in ticket: HTTP GET, PUT, DELETE (not POST).
	- Any user with URL can invoke permitted operations.
- Example using private account key and gcloud storage;
`gcloud storage signurl -d 10m path/to/privatekey.p12 gs://bucket/object`

