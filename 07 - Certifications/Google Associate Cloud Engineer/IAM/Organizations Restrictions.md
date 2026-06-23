Let you prevent data exfiltration through phishing or insider attacks.
For managed devices in an organization, the Organization Restrictions feature restricts access only to resources in authorized Google Cloud organizations.

Google Cloud administrators who administer Google Cloud, and egress proxy administrators, who configure the egress proxy, engage together to set up organization restrictions.

The managed device is governed by the organizational policies of a company. An egress proxy administrator configures the proxy to add organization restrictions headers to any requests originating from a managed device. This proxy configuration prevents users from accessing any Google Cloud resources in a non-authorized Google Cloud organization.

Organization Restrictions can be used to restrict access to employees in your organization so that employees can access resources only in your Google Cloud organization and not other organizations. They can also be used to allow your employees to read from Cloud Storage resources but restrict employee access only to resources in your Google Cloud organization. Or, allow your employees to access a vendor Google Cloud organization in addition to your Google Cloud organization.