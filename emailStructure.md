This file covers the standard structure of an html email.

## Table of contents

1. [Overview](#overview)
2. [DOCTYPE](#doctype)
2. [html tag](#html)
3. [head tag](#head)
3. [meta tag](#meta)
4. [style tag](#style)
5. [body tag](#body)
6. [outer table](#outertable)

### [Overview](#overview)

While web standards have progressed and the web development community has generally embraced the transition to HTML5, HTML email has largely been stuck in the past due to a relatively large number of email clients and lack of consensus between them on what each client will interpret, strip out, replace, or disregard in your html email. 

As such, much of what you will be doing when creating html emails will be contrary to what you would do if you were creating an html web page. While the approach is similar, the implementation is different. For instance, the layout of an HTML email and an HTML web page both follow a structure similar to below:

  <!DOCTYPE>
  <html lang="en">
    <head>
      <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
      
      <style>
        <!--INSERT YOUR EMBEDDED STYLE ATTRIBUTES HERE-->
      </style>
    </head>
    <body>
      <!--INSERT THE BODY OF YOUR EMAIL/WEB PAGE HERE-->
      
      
    </body>
  </html>


### [DOCTYPE](#doctype)

The DOCTYPE is one of your opportunities to attempt to preserve the integrity of your email when it is rendered by the email client. You want to make some DOCTYPE declaration so that the browser/email client can interpret how you want your html email to be served and will do so in 'standards' mode, instead of 'quirks' mode. General consensus in the HTML email community is to use the XHTML 1.0 transitional Document Type Declaration as it results in a more predictably rendered email. 

Your DOCTYPE declaration can be written as follows: 

`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">`

### [html tag](#html)


