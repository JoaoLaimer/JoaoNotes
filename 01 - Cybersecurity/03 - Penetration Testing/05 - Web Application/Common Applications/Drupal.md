## Discovery/Footprinting
A Drupal website can be identified in several ways, including by the header or footer message `Powered by Drupal`, the standard Drupal logo, the presence of a `CHANGELOG.txt` file or `README.txt file`, via the page source, or clues in the robots.txt file such as references to `/node`.
```shell
 curl -s http://drupal.inlanefreight.local | grep Drupal

<meta name="Generator" content="Drupal 8 (https://www.drupal.org)" />
      <span>Powered by <a href="https://www.drupal.org">Drupal</a></span>
```
Another way to identify Drupal CMS is through [nodes](https://www.drupal.org/docs/8/core/modules/node/about-nodes). Drupal indexes its content using nodes. A node can hold anything such as a blog post, poll, article, etc. The page URIs are usually of the form `/node/<nodeid>`.

Drupal supports three types of users by default:

1. `Administrator`: This user has complete control over the Drupal website.
2. `Authenticated User`: These users can log in to the website and perform operations such as adding and editing articles based on their permissions.
3. `Anonymous`: All website visitors are designated as anonymous. By default, these users are only allowed to read posts.
## Enumeration
Newer installs of Drupal by default block access to the `CHANGELOG.txt` and `README.txt` files, so we may need to do further enumeration. Let's look at an example of enumerating the version number using the `CHANGELOG.txt` file. To do so, we can use `cURL` along with `grep`, `sed`, `head`, etc.

## Attacking Drupal
## Leveraging the PHP Filter Module

In older versions of Drupal (before version 8), it was possible to log in as an admin and enable the `PHP filter` module, which "Allows embedded PHP code/snippets to be evaluated." From here, we could tick the check box next to the module and scroll down to `Save configuration`. Next, we could go to Content --> Add content and create a `Basic page`. We can now create a page with a malicious PHP snippet.

From version 8 onwards, the [PHP Filter](https://www.drupal.org/project/php/releases/8.x-1.1) module is not installed by default. To leverage this functionality, we would have to install the module ourselves. Since we would be changing and adding something to the client's Drupal instance, we may want to check with them first. We'd start by downloading the most recent version of the module from the Drupal website.
```shell
$ wget https://ftp.drupal.org/files/projects/php-8.x-1.1.tar.gz
```
Once downloaded go to `Administration` > `Reports` > `Available updates`.
From here, click on `Browse,` select the file from the directory we downloaded it to, and then click `Install`.

## Uploading a Backdoored Module