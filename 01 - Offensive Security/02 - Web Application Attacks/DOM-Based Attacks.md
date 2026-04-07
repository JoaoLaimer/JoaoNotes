DOM refers to the Document Object Model, which is the programming interface that displays the web document. When you make a request to a web application, the HTML in the response is loaded as the DOM in the browser. In essence, the DOM is the programmatic view of the web application that the user sees in their browser. Once loaded, JavaScript can interface with the DOM and make updates to change what the user sees. The DOM has a tree-like structure, allowing developers to use JavaScript code to search it or modify specific elements.

With the rise of modern frontend frameworks, birth was given to a new web application model called the single page application (SPA). SPAs are loaded only once when the user visits the website for the first time, and all code is loaded in the DOM. Leveraging JavaScript, instead of reloading the DOM with each new request made, the DOM is automatically updated.

## The Source and the Sink
Source: the location where untrusted user input made its way into the data pipeline.
Sink: the function where untrusted user input is reflected back in the application, leading to a successful attack.

## DOM-based Open Redirection

Let's say that the frontend developers are using information from the # value to determine the location of navigation for the web application. This can lead to a DOM-based open redirect. Let's take a look at an example of this in JavaScript code:

`goto = location.hash.slice(1) if (goto.startsWith('https:')) {   location = goto; }`

The source in this example is the `location.hash.slice(1)` parameter which will take the first # element in the URL. Without sanitisation, this value is directly set in the `location` of the DOM, which is the sink. We can construct the following URL to exploit the issue:

`https://realwebsite.com/#https://attacker.com`[](https://realwebsite.com/#https:/attacker.com)

Once the DOM loads, the JavaScript will recover the # value of https://attacker.com and perform a redirect to our malicious website.

## DOM-based XSS
The most common source for DOM-based XSS is the URL and, more specifically, URL fragments, which are accessed through the `window.location` source. This is because we have the ability to craft a link with malicious fragments to send to users. In most cases, fragments are not interpreted by the web server but reflected in the response, leading to DOM-based XSS. However, it should be noted that most modern browsers will perform URL encoding on the data, which can prevent the attack. This has led to a decrease in the prevalence of these types of attacks through the URL as source.

`https://realwebsite.com#<img src=1 onerror=alert(1)></img>`

This is one example of how XSS can be performed. However, several other sinks could be used. This includes normal JavaScript sinks and framework-specific ones such as those for jQuery and Angular. For a complete list of the available sinks, you can visit [this page](https://portswigger.net/web-security/cross-site-scripting/dom-based).