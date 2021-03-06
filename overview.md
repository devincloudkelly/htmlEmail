## Overview

This file provides a high-level overview of best-practices for constructing an HTML email. For each section of your document, code is provided to use for boilerplate HTML email development, or for the basis of your own template. 

The standards detailed in this overview come from personal experience, the resources linked to throughout this document, and an informal survey comparing code across a variety of HTML emails found on [Really Good Emails](https://reallygoodemails.com/). Full details of this survey [can be found here](emailSurvey.md)

## Table of contents

1. [HTML Email Layout](#html-email-layout)
2. [DOCTYPE](#doctype)
2. [html tag](#html-tag)
3. [head tag](#head-tag)
3. [title tag](#title-tag)
3. [meta tag](#meta-tag)
4. [style tag](#style-tag)
4. [script tag](#script-tag)
5. [body tag](#body-tag)

## [HTML Email Layout](#layout)

To begin, HTML email development is not the same as web development. They are related, but each has evolved down a separate path.

While web standards have progressed and the web development community has generally embraced the transition to successively more performant and modern forms of HTML and CSS, HTML email has largely been stuck in the past. This is due to a relatively large number of email clients and lack of consensus between them on what each client will interpret, strip out, replace, or disregard in your HTML email.

As such, much of the code you will be writing when creating HTML emails will be contrary to what you would do if you were creating an HTML web page. While the approach is similar, the implementation is different. 

For instance, the high-level layout of an HTML email and an HTML web page both follow a similar structural approach. The simplified structure below can serve as a starting point for either an HTML email or web page:

    <!DOCTYPE >
    <html lang="en">
      <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
        <!--INSERT OTHER META TAGS HERE-->
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

## [DOCTYPE](#doctype)

The DOCTYPE is one of your opportunities to attempt to preserve the integrity of your email when it is rendered by the email client. You want to make some DOCTYPE declaration so that the browser/email client can interpret how you want your html email to be served and will do so in 'standards' mode, instead of 'quirks' mode. 

If you're optimizing your HTML email for all email clients, or you're just getting started and looking for a good place to start, general consensus in the HTML email community is to use the XHTML 1.0 transitional Document Type Declaration as it results in a more predictably rendered email. 

Your DOCTYPE declaration can be written as follows: 

`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">`

The above `<DOCTYPE>` declaration isn't the only one you can use. Plenty of HTML email developers use some variant of the HTML 4.01 Document Type Declaration. If in doubt, start with XHTML 1.0 Transitional (shown above), then change it up as you get more comfortable with HTML email.

For more on `DOCTYPE`s, view the [W3 wiki](https://www.w3.org/wiki/Doctypes_and_markup_styles).

## [html tag](#html)

The `<html>` tag is where you can declare the language for your document, ex. `lang="en"` for English. It is also where you can declare XML namespaces. Let's go over the attributes you should include in every HTML email.

### Language

This is a simple one and easy to overlook, but be sure you include it. This attributes sets the language of the text in your email and is especially useful for subscribers who are using assistive devices, such as screen readers, allowing the device to be read in the correct language. If this isn't set, the `lang` attribute could default to a language different than intended.

For example, if an American subscriber subscribes to a French newsletter and the `lang` attribute on that newsletter isn't set as `lang="fr"`, the user's email client may interpret it into the user's local language, English. If they were using a screen-reader, this would lead to a very poor experience for the user.

What if your email has multiple languages in it? Let's say you're sending out an email for your language tutoring courses, and wanted to include the phrase "How are you?" in multiple languages? In this case, you would set the `lang` attribute in your `html` element to the predominant language of the email, then specify a different language in a  `span` element for any text in a different language like the example below:

    <html lang="en" xmlns="http://www.w3.org/1999/xhtml">
        <body>
            <!--Main content of your email-->
            <p>How are you?</p>
            <p><span lang="fr">Comment t'allez vous?</span></p>
            <p><span lang="vi">Bạn khỏe không?</span></p>
        </body>
    </html>   

\* Note, you could set the `lang` in the `<p>` element directly, but if you had other attributes in that element with text values, setting the `lang` attribute would change the language for *those attributes* as well. For that reason, it's safest to wrap just the text in a `<span>` and set the `lang` there.

For more on setting the `lang` attribute in your HTML document, refer to the [W3 documentation](https://www.w3.org/International/questions/qa-html-language-declarations).

### XML Namespaces
XML namespaces are used to define and discern between elements that share the same name. You can think of them as different "libraries" of elements for you to use in your HTML document. 

Since HTML email development involves developing for disparate clients, adding in several XML namespaces in your `<html>` tag allows you to use these different "libraries" and access new elements to help you create emails that render well across clients. If you're looking for more detail on [XML namespaces](https://www.sitepoint.com/xml-namespaces-explained/), check out this article by Ian Stuart. 

One of the common sticking-points for HTML email developers is Outlook. Most versions of Outlook are now rendered by Microsoft Word (yes, that Microsoft Word) and as such, they don't display HTML elements as intuitively as you'd like. To get around this, its common to code fallbacks for the sections of your email that aren't rendering properly in Outlook. For this, you might want to add the following namespace: 

    xmlns:o="urn:schemas-microsoft-com:office:office"

Note the `:o` after `xmlns`. This is a prefix and it allows you to designate which namespace the element you are using in your HTML document belongs to. For instance, if `<table>` exists in two namespaces, the code below references the `<table>` element that is found in the XML namespace you designated as `xmlns:o`.

    <o:table>
      <o:tr>
        <o:td>
        </o:td>
      </o:tr>
    </o:table>

Another common XML namespace to include would be the one for VML. When you want a reliable background image in your HTML email, VML works great. You can add it with the following: 

    xmlns:v="urn:schemas-microsoft-com:vml"

Again, you need to add some designation after the  `xmlns` to allow you to differentiate between namespaces in your HTML document.

Based on what your email goals are, there are two good starting places. If Outlook is not a consideration for your email goals, you can just use the standard XML namespace declaration: 

    <html lang="en" xmlns="http://www.w3.org/1999/xhtml">

If, however, you will be designing emails with Outlook in mind, I'd recommend including the `office` and `vml` XML namespaces as you'll likely need them.

    <html lang="en" xmlns="http://www.w3.org/1999/xhtml" xmlns:o="urn:schemas-microsoft-com:office:office" xmlns:v="urn:schemas-microsoft-com:vml">
 
## [head tag](#head)

The `<head>` element will contain metadata about your HTML document. 

    <head>
       <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Insert Title for viewing email in Browser</title>
       <style type="text/css">
        <!--INSERT EMBEDDED CSS HERE-->
        <!--ADD @MEDIA QUERIES FOR MOBILE RESPONSIVENESS-->
       </style>
    </head>

That metadata will be nested between your opening and closing `<head></head>` tags and will commonly include a `<title>` tag for setting the title on browser views, `<meta>` tags for defining `Content-Type` and `viewport`, and `<style>` tags for your embedded CSS.

## [title tag](#title)

This one has limited use, but is still important. First, it is great for accessibility and provides a title for your HTML email for subscribers who are using an assistive device. The `<title>` element is nested between your `<head>` tags.

Second, if someone opens your email in the browser, this title will show up on the tab. An example `<title>` tag might look like this: 

    <head>
      <title>How to code an HTML email</title>
    </head>

## [meta tag](#meta)

For `<meta>` tags, there are two that are commonly used; one to define your `Content-Type` and one to define your `viewport`. The `<meta>` element is nested inside your `<head>` element.

     <head>
       <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
     </head>

The `<meta>` tag that sets your `Content-type` is used to ensure your document is parsed properly by the browser/email client, so you should include this in every document. 

The tag for the `viewport` is important for optimizing for mobile and since the majority of subscribers now access email primarily on their phone, this tag should also be included in every document. Further info on this tag can be [found on MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Mobile/Viewport_meta_tag).

### Other useful tags

If you are optimizing for Windows Phones 7.5 or higher, then you'll want to include the following `<meta>` tag, as it enables CSS3 and media queries for those devices: 

    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    
When your emails render on iOS you'll notice that it automatically detects phone numbers and dates, styles them as a link and allows you to click them to initiate a call or add to your calendar. 

Most of the time, this is a great built-in feature, but if you are sending other important numbers that look like phone numbers, such as account numbers, or you want subscribers to click on a CTA to learn more about an event (instead of saving it to their calendar), you'll want to disable these features. 

You can add the following `meta` tags to tell iOS not to automatically detect and format phone numbers and dates:

    <meta name="format-detection" content="telephone=no">
    <meta name="format-detection" content="date=no">

## [style tag](#style)

The `<style>` element is where you can add your embedded CSS. With HTML emails, CSS is not as globally supported as it is in web browsers, so the most common methods for adding CSS styling are embedded CSS (CSS added inbetween your `<style>` tags) and inline CSS (CSS written inline in a `<style>` attribute in your HTML elements). Linking to external stylesheets produces mixed results and is generally avoided.

Depending on the email clients you are designing your emails for, the `<style>` element will include common CSS styles for HTML elements and classes, `@media` queries for mobile-responsiveness, and separate stylesheets for disparate email clients, commonly for Outlook.

TIP: I've experienced rendering issues with Gmail on Mobile (specifically with the Pixel) where the email doesn't render as mobile responsive and instead renders the desktop version. I've found this [separate style tags solution on Litmus' forum](https://litmus.com/community/discussions/7437-media-queries-not-rendering-on-gmail-mobile-app) which works great (thanks [Olga Kham](https://ca.linkedin.com/in/olga-kham)!) Separating your media query style resets into their own `<style>` tag gets around the issue where the Gmail mobile app strips out unsupported code. In practice, I now put every distinct set of style resets in their own tag (ex. desktop, mobile, outlook..)

       
       <!--STYLING RESETS FOR DESKTOP / NON-MOBILE FORMATS-->
       <style type="text/css">
                  
        h1 {
         font-size: 22px;
         line-height: 30px;
        }
        p {
         font-size: 16px; 
         line-height: 20px;
        }
        table {
         border: 0 !important;
        }
        .desktop-button {
         width: 50%;
        }
       </style>
        
        
       <!--STYLING RESETS FOR MOBILE USING MEDIA QUERIES-->
        
       <style type="text/css">
        <!--Media queries for mobile-responsiveness-->
        
        @media only screen and (max-width: 660px) {
         .mobile-center {
          text-align: center !important;
         }
        } 
       </style>
       
       
       <!--SEPARATE STYLESHEET FOR OUTLOOK-->
       
       <!--[if mso]>
        <style>
         p {
          font-size: 100% !important;
         }
       </style>
       <[endif]-->

## [script tag](#script)

Unfortunately for email marketers, `<script>` elements are not widely supported in most email clients. There are a few notable exceptions, such as Google and their Gmail promotions tab, but for now, know that `<script>` tabs likely will be stripped out or not work in your email, and should be avoided. 

If needed, in place of `<script>` elements you can often use microdata in the `<body>` of the email. See [microdata example](https://developers.google.com/gmail/promotab/troubleshooting#script_tags_get_stripped_by_your_email_service_provider) for Gmail promotions tab.

## [body tag](#body)

We're finally here - we can now start to build out our email. The `<body>` of your email will look something like this:

    <body width="100%">
        <div style="display: none; max-height: 0; overflow: hidden;">INSERT YOUR PREHEADER TEXT HERE</div>
        <table class="outer-container" border="0" cellspacing="0" cellpadding="0" width="100%">
            <tr>
                <td width="600px" >
                    <!--CONTENT OF YOUR EMAIL GOES HERE-->
                </td>
            </tr>
        </table>
    </body>
    
We'll go into detail below, but know that HTML email consists of levels and levels of nested table elements. Unlike HTML for web development where `<div>`s are the predominant structural element, you will be structuring all layouts with `<table>`s. 

You will generally have an outer container to set the overall dimensions of your email, then use `<table>`, `<tr>`, and `<td>` elements to define new sections, rows and columns. 

### Body and Outer Container

The construction of the `<body>` tag and the first `<table>` tags are important as they will be used to define the overall structure of your email. It is considered best practice to set the `<body>` width to 100% and then set the width of your email in your outer table.

This outer `<table>` is commonly referred to as an `outer` or `wrapper` table and is meant as a first line of defense against Email Clients. Some will strip out the body tag, so the outer `<table>` is important to ensure your email width is set properly. Follow the example above and set the outer `<table>`s width to 100%, and then set the overall width of your email in the `<td>` element of your outer table. 

A note about email widths. Industry best practice recommends between 400-600px width for your emails. Going much over 600px will lead to rendering issues across devices, while going too small decreases the size of the canvas you can work with. I'd recommend starting at 600px then adjusting as needed.

### Table Structure

In reviewing emails across industries, there seem to be two main approaches to structuring your emails. The `table`/`tr`/`td` structure and the `table`/`tbody`/`tr`/`td` structure. I'd recommend using `table`/`tr`/`td` structure for two reasons. First, it cuts out an unnecessary layer which helps to reduce confusion, especially when writing your first HTML emails. Second, the `<tbody>` tag isn't supported in all email clients, so not using it removes the requirement for additional fallbacks coded into your email.

As far as I can tell, those using the `table`/`tbody`/`tr`/`td` structure are predominantly ESPs, likely using `<tbody>` tags for some dynamic effect related to their email software. For 'handwritten' HTML emails, I go with the recommendations of Litmus and Email on Acid and prefer the simpler, more bulletproof `table`/`tr`/`td` structure.

### Nested Tables

The body of your email will follow a structure similar to below: 

    <body>
        <!--THIS FIRST TABLE WILL BE YOUR OUTER CONTAINER-->
        <table class="outer">
            <tr>
                <td>
                <!--INSIDE THIS CELL IS WHERE YOU'LL ADD ALL OF YOUR EMAIL CONTENT-->
                <table class="header">
                    <tr>
                        <td>
                            <!--ADD HEADER CONTENT HERE-->
                        </td>
                    </tr>
                </table>
                <table class="header">
                    <tr>
                        <td>
                            <!--ADD BODY CONTENT HERE-->
                        </td>
                    </tr>
                </table>
                <table class="header">
                    <tr>
                        <td>
                            <!--ADD FOOTER CONTENT HERE-->
                        </td>
                    </tr>
                </table>
                </td>
            </tr>
        </table>
    </body>

All of your content will be housed in a `<td>` element.

