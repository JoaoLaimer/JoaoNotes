Google Dorking is the name given to the advanced technique to searching on Google. 
Dorks are the name given to google's own terms for it's own built-in query language, which helps us to filter the searches.
Here it's some examples:
- **site** : Tells google to show you results from a certain site only.
- **inurl**: Searches pages with a URL that match the search string.
- **intitle**: Finds specific strings ina page's title.
- **link**: Searches for web pages that contains link to a specified URL.
- **filetype**: Searches for pages with a specific file extensions.
- **Wildcard**: The * operator within searches mean any character or series of characters.
- **Quotes (" ")**: Adding quotations marks around your search terms forces an exact match. Not necessarily together.
- **Minus (-)**: Excludes certain search results.

Examples:
- Look for all of a company's subdomains:
`site:*.example.com `
- Look for a kibana dashboard:
`site:example.com inurl:app/kibana`
- Look for a S3 Bucket:
`site:s3.amazonaws.com COMPANY_NAME`
- Look for passwords:
`site:example.com ext:txt password`

