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

While web standards have progressed and the web development community has generally embraced the transition to HTML5, HTML email has largely been stuck in the past due to a relatively large number of email clients and lack of consensus between them on what each client will interpret, strip out, replace, or disregard in your HTML email. 

As such, much of the code you will be writing when creating HTML emails will be contrary to what you would do if you were creating an HTML web page. While the approach is very similar, the implementation is different. For instance, the high-level layout of an HTML email and an HTML web page both follow a similar structural approach. The simplified structure below can serve as a starting point for either an HTML email or web page:

    <!DOCTYPE>
    <html lang="en">
      <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
        <!--INSERT OTHER META TAGS AND SCRIPTS HERE-->
        <style>
          <!--INSERT YOUR EMBEDDED STYLE ATTRIBUTES HERE-->
        </style>
      </head>
      <body>
        <!--INSERT THE BODY OF YOUR EMAIL/WEB PAGE HERE-->
      
      
      </body>
    </html>

Once you start building out the individual elements of your HTML email, however, the differences between developing for HTML email and developing for the web become vastly apparent. 

For instance, in web development, page elements are structured in `<div>` tags and often make heavy use of CSS features such as `grid` or `flexbox` to optimize their layout. 

In HTML email development on the other hand, `<table>` tags are the dominant layout element as they render more reliably across more email clients than `<div>` tags and HTML tag attributes are used more frequently in addition to CSS to provide a more reliably rendered email.
    
We will go over each part of an HTML email below in more detail, but for now, just know that HTML email development should feel familiar at a high-level, but you should be prepared to embrace the 'quirks' of HTML email development at the implementation level. 

Each part of your HTML email document will require a new approach if you are coming from a web development perspective, and much of it may feel like a trip down memory lane if you have worked with past versions of HTML, or a history lesson to those new to the community.

You can navigate directly to an HTML email section by using the table of contents above, or you can continue on to read through all sections from top to bottom. 

### [DOCTYPE](#doctype)

The DOCTYPE is one of your opportunities to attempt to preserve the integrity of your email when it is rendered by the email client. You want to make some DOCTYPE declaration so that the browser/email client can interpret how you want your html email to be served and will do so in 'standards' mode, instead of 'quirks' mode. General consensus in the HTML email community is to use the XHTML 1.0 transitional Document Type Declaration as it results in a more predictably rendered email. 

Your DOCTYPE declaration can be written as follows: 

`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">`

### [html tag](#html)


