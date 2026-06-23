- Custumer-supplied encryption key (CSEK)
- Object Lifecycle Management
- Object Versioning
- Directory synchronization
- Object change notification using Pub/Sub
- Autoclass

## Object Versioning supports the retrieval of objects that are deleted or overwritten
- Objects are immutable
- Object Versioning
	List archived versions of an object, restore an object to an older state, or delete a version.

## Soft Delete
Provides default bucket-level protection from:
- Accidental deletion
- Malicious deletion
Retains overwritten or changed data.
Is enabled by default with a 7 day retention duration.

## Object Lifecycle Management Policies specify actions to be performed on objects that meet certain rules.

## Object Retention Lock
- Lets you define data retention requirements on a per-object basis.
- Retention configuration governs how long the object must be retained.

## Data Import Services
- **Transfer Appliance**: Rack capture and the ship your data to Google Cloud.
- **Storage Transfer Service**: Import online data (another bucket, an S3 bucket, or web source).
- **Offline Media Import**: Third-party provider uploads the data from physical media.
