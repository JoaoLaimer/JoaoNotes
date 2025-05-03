Description: Use your exploitation skills to bypass authentication mechanisms on a website and get RCE.

First Step: Reconnaissance.
I first ran the normal SYN Stealth Scan: 
![[HammerReconIMG.png]]
But unfortunately only SSH showed up in my scan, so I tried again but with with all ports to see if something shows up, as we are not worried for being detected I ran it in insane mode for a faster scan:
`nmap -A <IP> -p- -T5`
![[HammerRecon2IMG.png]]
We can see port 1337 is open for a http server.
Accessing the server we are presented with a simple login form:![[HammerIMG.png]]
We can run a few tests to see what we are dealing with. When we try any email and password combination the site prompts: "Invalid Email or Password!". So we can't enumerate credentials by inserting a correct email and expecting it to tell us just the password is wrong. We also have a "Forgot your password?" page:![[Hammer2IMG.png]]
Having a look at the page source we can see a little dev note:![[Hammer3IMG.png]]
We might be able to fuzz any extra directory with this information, let's use `ffuf` to do it.
The command goes as follows: `ffuf -u http://<IP-Address>:1337/hmr_FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt

We found some directories we can visit!![[Hammer4IMG.png]]
Visiting hmr_images just gives us an image of an hammer, so maybe that's no use for now.
hmr_css and hmr_js also gives as nothing. But, hmr_logs, reveals us an email address we can use on the site!![[Hammer5IMG.png]]
Great we found some goodies. Something was being done on the `/var/www/html/` directory, and we found the address: `tester@hammer.thm`.
If we use this new found email, we can try to reset it's password:![[Hammer6IMG.png]]
Just 4-Digits and 180 seconds before refreshing the password, we can try brute-forcing it. I'll be using BurpSuite for it. 
While intercepting the requests and responses I've noticed the countdown was being handled on the client-side, so by modifying the field we might get more time to guess the code.![[Hammer7IMG.png]]![[Hammer8IMG.png]]
I configured the attack so that the recovery_code goes from 0000 to 9999 and the `s` is lower to what is now in the browser so that the check in the Javascript code doesn't try to log us out.
![[Hammer9IMG.png]]
Let's start the attack!
One thing that happened is that we received a timeout even though we previously taught it was all client-side so we really have 180 seconds. Let's try again.
The first 5 requests went through, but, the rest were being rate limited. Shame. 
At this stage I didn't really know what to do, so, research time! ![[Hammer10IMG.png]]
I've came across this medium [article](https://medium.com/@raxomara/bypassing-rate-limits-all-known-techniques-25891bb5ca59) that has some techniques we can use to bypass the rate limit.
The first technique is "Adding Custom Header (X-Forwarded-For, X-Real-IP)".
In this technique we can just add a new header with any IP to trick the server into thinking requests come from different IPs. Let's try using it.
Before trying to make a script, let's take a look at the response of a failed attempt so we can filter it.
"Invalid or expired recovery code!"
Let's use "Invalid" and "expired" as the filtering words, and build the script.![[Hammer12IMG.png]]
In this script I've created an array of numbers from 0000 to 9999, and created 50 threads to post request for each number with an random IP-address attached to the "X-Forwarded-For" header, also an important thing to notice is that we are also sending the session token in the "Cookie" header.
Once an possible valid code is found we can use it in the "4-Digit Code" field.
![[Hammer11IMG.png]]Resetting the password to something simple should do the trick, now we can log in and get the first flag!![[HammerFlag1IMG.png]]
Strangely, the site redirects us to the login page after a while... Looking into the source of the page we can see it has a script that after some time tries to get the "persistentSession" value and if it's false, log us out.
``` html
	<script>
       
        function getCookie(name) {
            const value = `; ${document.cookie}`;
            const parts = value.split(`; ${name}=`);
            if (parts.length === 2) return parts.pop().split(';').shift();
        }
      
        function checkTrailUserCookie() {
            const trailUser = getCookie('persistentSession');
            if (!trailUser) {
          
                window.location.href = 'logout.php';
            }
        }
       
        setInterval(checkTrailUserCookie, 1000); 
    </script>
```
Unfortunately, I couldn't make the site persist, without breaking the "Enter Command" functionality, so I guess we just have to deal with it.
Before continuing other important thing I've found in the source is a JWT token.
``` html
<script>
$(document).ready(function() {
    $('#submitCommand').click(function() {
        var command = $('#command').val();
        var jwtToken = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiIsImtpZCI6Ii92YXIvd3d3L215a2V5LmtleSJ9.eyJpc3MiOiJodHRwOi8vaGFtbWVyLnRobSIsImF1ZCI6Imh0dHA6Ly9oYW1tZXIudGhtIiwiaWF0IjoxNzQ2Mjk0OTE5LCJleHAiOjE3NDYyOTg1MTksImRhdGEiOnsidXNlcl9pZCI6MSwiZW1haWwiOiJ0ZXN0ZXJAaGFtbWVyLnRobSIsInJvbGUiOiJ1c2VyIn19.72j26KuUU7dq1IU_DWPjqYxRjrCUCn5UhvGS1PdLh9k';
        // Make an AJAX call to the server to execute the command
        $.ajax({
            url: 'execute_command.php',
            method: 'POST',
            data: JSON.stringify({ command: command }),
            contentType: 'application/json',
            headers: {
                'Authorization': 'Bearer ' + jwtToken
            },
            success: function(response) {
                $('#commandOutput').text(response.output || response.error);
            },
            error: function() {
                $('#commandOutput').text('Error executing command.');
            }
        });
    });
});
</script>
```

Apparently to execute the command the JWT is responsible for the authorization. We can also see the full request the client makes to the server.
We may have to tamper with the JWT to get more commands to work.
Using [jwt.io/](https://jwt.io/) we can see whats inside the token: ![[Hammer14IMG.png]]
Back in the dashboard, entering some commands I've just got `ls` to work, which reveals some files to us.
![[Hammer13IMG.png]]
The `188ade1.key` file might just be what we need to sign the token and change our role to admin.
We can download it by inserting it into the url, like so: `http://<IP-Address/>:1337/188ade1.key`
![[Hammer15IMG.png]]
We can try to copy the key content into the 256-bit secret of the JWT and see if it works.
We may also change the "kid" header of the token to point to where we downloaded the key. Remembering the log file of the first steps, we can see the tester account was in the `/var/www/html/` directory, this may indicate where the key is actually located, also, I've tried running `pwd` in the dashboard but it got denied.
![[Hammer16IMG.png]] With our new JWT in hands, let's try altering it and executing `cat /home/ubuntu/flag.txt` to retrieve the last flag!
![[Hammer17IMG.png]]
Modifying the JWT in the response didn't work, the only way I got this working was by modifying the execute command request, changing only the "Authorization" header, and the command (obviously). ![[HammerFlag2IMG.png]]
And just like that we got the second flag!
This was a really fun room, putting in practice what I've learned about Session Management, Brute Forcing and JWT Security from the Web Penetration Testing learning path, and took a little bit of researching which I don't mind at all. 