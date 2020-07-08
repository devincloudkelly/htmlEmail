This file covers the standard structure of an html email.

## Table of contents

1. [Overview](#overview)
2. [DOCTYPE](#doctype)
2. [html tag](#html)
3. [head tag](#head)
3. [meta tag](#meta)
4. [style tag](#style)
4. [script tag](#script)
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
    
We will go over each part of an HTML email below in more detail, but for now, just know that HTML email development should feel familiar at a high-level, but you should be prepared to embrace the 'quirks' of HTML email development at the implementation level. HTML email development is largely a matter of developing for multiple clients, which may include simplifiying your designs, supporting only certain clients based on your subscriber data, and creating media queries and fallbacks for certain email clients.

Each part of your HTML email document will require a new approach if you are coming from a web development perspective, and much of it may feel like a trip down memory lane if you have worked with past versions of HTML, or a history lesson to those new to the community.

You can navigate directly to an HTML email section by using the table of contents above, or you can continue on to read through all sections from top to bottom. 

### [DOCTYPE](#doctype)

The DOCTYPE is one of your opportunities to attempt to preserve the integrity of your email when it is rendered by the email client. You want to make some DOCTYPE declaration so that the browser/email client can interpret how you want your html email to be served and will do so in 'standards' mode, instead of 'quirks' mode. General consensus in the HTML email community is to use the XHTML 1.0 transitional Document Type Declaration as it results in a more predictably rendered email. 

Your DOCTYPE declaration can be written as follows: 

`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">`

### [html tag](#html)

The `<html>` tag is where you can declare the language for your document, ex. `lang="en"` for English. It is also where you can declare XML namespaces.

XML namespaces are used to define and discern between elements that share the same name. You can think of them as different "libraries" of elements for you to use in your HTML document. 

Since HTML email development involves developing for disparate clients, adding in several XML namespaces in your `<html>` tag allows you to use these different "libraries" and access new elements to help you create emails that render well across clients. If you're looking for more detail on [XML namespaces](https://www.sitepoint.com/xml-namespaces-explained/), check out this article by Ian Stuart. 

One of the common sticking-points for HTML email developers is Outlook. Most versions of Outlook are now rendered by Microsoft Word (yes, that Microsoft Word) and as such, they don't display HTML elements as intuitively as you'd like. To get around this, its common to code fallbacks for the sections of your email that aren't rendering properly in Outlook. For this, you might want to add the following namespace: 

    xmlns:o="urn:schemas-microsoft-com:office:office

Note the `:o` after `xmlns`. This is a prefix and it allows you to designate which namespace the element you are using in your HTML document belongs to. For instance, if `<table>` exists in two namespaces, the code below references the `<table>` element that is found in the XML namespace you designated as `xmlns:o`.

    <o:table>
      <o:tr>
        <o:td>
        </o:td>
      </o:tr>
    </o:table>

Another common XML namespace to include would be the one for VML. When you want a reliable background image in your HTML email, VML works great. You can add it with the following: 

    xmlns:v="urn:schemas-microsoft-com:vml

Again, you need to add some designation after the  `xmlns` to allow you to differentiate between namespaces in your HTML document.

You'll have to confirm which email clients you are targeting and your email goals to determine which XML namespaces to include, but here's a good starter if you plan on using a VML background: 

    <html lang="en" xmlns="http://www.w3.org/1999/xhtml" xmlns:v="urn:schemas-microsoft-com:vml">
 
### [head tag](#head)

The `<head>` element will contain metadata about your HTML document. 

That metadata will be nested between your opening and closing `<head></head>` tags and will commonly include `<meta>` tags for settings such as the device viewport, `<style>` tags for your embedded CSS, and `<script>` tags which are useful for things like annotating your email for a richer user experience in Gmail's promotions tab.

### [meta tag](#meta)

For `<meta>` tags, there are two that are commonly used; one to define your `Content-Type` and one to define your `viewport`.

     <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0" />

The `<meta>` tag that sets your `Content-type` is used to ensure your document is parsed properly by the browser/email client, so you should include this in every document. 

The tag for the `viewport` is important for optimizing for mobile and since the majority of subscribers now access email primarily on their phone, this tag should also be included in every document. Further info on this tag can be [found on MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Mobile/Viewport_meta_tag).

