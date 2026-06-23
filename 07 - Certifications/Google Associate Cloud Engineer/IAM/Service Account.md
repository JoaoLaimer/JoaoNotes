Service accounts provide an identity for carrying out service-to-service interactions.
- Program running within Compute Engine instances can automatically acquire access tokens with credentials.
- Tokens are used to access any service API in your project and any other services that granted access to that service account.
- Service accounts are convenient when you're not accessing user data.

Service accounts are identified by an email address
- `12345678910-compute@project.gserviceaccounte.com`
- Three types of service accounts:
	- Built-in
	- user-created (Custom)
	- Google APIs service account
Default Compute Engine service account
- Automatically create per project with auto-generated name and email address.
- Automatically added as a project editor
- By default, enabled on all instances created using gcloud or the Google Cloud console.


## Scopes
Scopes are used to determine whether an authenticated identity is authorized.

## Service account permissions
- Default service accounts: basic and predefined roles
- User-created service accounts: predefined roles
- Roles for service accounts can be assigned to groups or users.

## Service Account Keys
**Google-managed service accounts**
- All service accounts have Google-managed keys.
- Google stores both the public and private portion of the key.
- Each public key can be used for signing for a maximum of two weeks.
- Private keys are never directly accessible.
**User-managed service accounts**
- Google only stores the public portion of a user-managed key.
- Users are responsible for private key security.
- Can create up to 10 user-managed service account keys per service.
- Can be administered via the IAM API, gcloud, or the console.
