Take a look at a company's third-party hosting footprint. Like S3 Buckets, Azure Blob. Those storage services can store logs, hidden endpoints, credentials, user information, etc.
One of finding those resources like S3 Buckets is through Google dorking. 

## AWS
### Simple Storage Service (S3)
Most S3 Buckets uses the URL format `BUCKET.s3.amazonaws.com` or `s3.amazonaws.com/BUCKET`, we can dork it.
`site:s3.amazonaws.com COMPANY_NAME`
`site:amazonaws.com COMPANY_NAME`

If the company uses custom URLs for its S3 buckets try more flexible terms instead.
```
amazonaws s3 COMPANY_NAME
amazonaws bucket COMPANY_NAME
amazonaws COMPANY_NAME
s3 COMPANY_NAME
```

Another way of finding buckets its searching in the company's public GitHub repositories for S3 URLs. Try searching these repositories for the term s3. 
We can use the `GrayhatWarfare` tool for finding public exposed s3 buckets. It allows you to search for a bucket by using a keyword. 
You can use `lazys3` tool to brute-force buckets by using wordlists.
Another tool is `Bucket Stream`, which parses certificates belonging to an organization and finds S3 buckets based on permutation of domain names.

Once found, we can use the `awscli` tool to see if you can access one.
Try listing the contents of the bucket:
`aws s3 ls s3://BUCKET_NAME/`
If this works try to read the contents by copying to your machine:
`aws s3 cp s3://BUCKET_NAME/FILE_NAME /path/to/local/directory`
Also try uploading content to it:
`aws s3 cp TEST_FILE s3://BUCKET_NAME`
And this command will remote files:
`aws s3 rm s3://BUCKET_NAME/TEST_FILE`
(NEVER DELETE COMPANY RESOURCES)

