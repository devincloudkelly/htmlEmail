## Summer 2020 Email Survey

Additional details are being added frequently. Check back for more updates!

### Instructions

- Download [Excel email comparison](Email-Construction-Comparison.xlsx)
- Follow along below while reviewing the comparison

## Purpose

While this was a relatively small (25 emails) comparison, it was useful to help draw out common patterns in optimal HTML email design as well as discover new use-cases and falllbacks. The purpose was to compare many of the common or frequent elements of modern, visually-impactful HTML emails to discover what works, what others are using, and ultimately, to learn more about HTML email development. 

There are HTML email elements that aren't covered in this survey and thats OK. This is not meant to be an end-all be-all overview. Instead, it is meant to give a quick insight into the current state of HTML email and be a good primer for current HTML email practices.

Let's dig in.

## Layout of Spreadsheet

Individual emails are laid out as columns, and the fields I am exploring are listed as rows. Totals are found in the last column and help to guide my overall discoveries.

The fields are divided into 4 sections: Email basics, HTML/Head, Style, and Body. 

The email basics section includes a link to the email's code on [Really Good Emails](https://reallygoodemails.com/), the Email Service Provider used to send that email (if known), and if the email is marked as NOT being mobile-friendly by RGE. 

This spreadsheet gives you a good overview of patterns, but looking at the individual source code of individual emails is incredibly valuable. I suggest you use this file comparison as a guide, then solidify your understanding by digging into the source code of individual emails - including your own emails!

## HTML/Head

### DOCTYPE

Overall, the majority of emails(15 out of 25) used the xhtml 1.0 transitional DOCTYPE, which has long been a standard for HTML emails. 3 had no DOCTYPE declaration, which is inadvisable, 3 declared HTML5, 2 declared html 4.01 strict, 1 declared xhtml 1.0 strict and 1 declared html 4.01 loose. 

Insights: Use the xhtml 1.0 transitional declaration for reliable rendering and a large online knowledgebase for support. HTML5 and html4.01 strict seem to be used for newer features of the languages but they will be harder to find solutions for online. 

### XML namespaces and attributes

Rows 7 thru 12 were used to track whether an XML namespace or attribute was present in the email's code or not. The one main takeaway from this assessment is that you should always include the basic `xmlns` `<meta>` element in your HTML email. The one exception to this is if you're using the HTML5 DOCTYPE, in which case XML namespace declarations are not required. 

The next most frequently used tags with 8 of the 25 emails using them were `xmlns:v` and `xmlns:o`, which are used primarily for dealing with Outlook. The takeaway from this is if you're optimizing your emails for viewing in Outlook, you will likely need to declare these namespaces in order to create fallbacks such as fallback buttons and fixing the Outlook DPI scaling issue.

4 of the 25 emails I looked at included XML namespaces for Facebook and OpenGraph. I did some investigating into them and they only appear in the head of the email and don't seem to be used for styling elements in the body of the email. It looks like these tags are used to add your email to Facebook and OpenGraph, which allows a browser version to be linked to with the purpose of making your content, in this case email, more shareable. OpenGraph is also used to help how your content appears in social media by explicitly declaring certain fields. 

Only 3 of the 25 emails included a `lang` attribute in their standard `xmlns` declaration. Especially as brands expand their reach globally and we should be optimizing for accessibility, the `lang` attribute should be included in every email and localized to the language the email is written in. 

### Other html and meta tags

Based on this survey, the `viewport` (used in 24/25) and `content-type` (used in 21/25) tags are definites.

    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0 ">

The `title` tag as only used by 15 out of 25, but is an easy one to include and should be used on all emails. Add a title to show up on the browser tab when your email is viewed in the browser.

    <title>INSERT YOUR TITLE HERE</title>

Another frequently used `meta` tag is the one that is used to enable CSS3 and media queries for Windows Phone 7.5 and higher. If you are targeting that device, include the following: 

    <meta http-equiv="X-UA-Compatible" content="IE=edge">
 
11 emails included a fix for a long-standing issue on certain versions of Outlook that causes your email to render erratically if the suscriber's display zoom is set to anything other than 100%. Obviously, if you're adding this fix, you are targeting Outlook. Feel free to skip if you aren't concerned about Outlook.

    <!--[if gte mso 9]><xml>
        <o:OfficeDocumentSettings>
        <o:AllowPNG/>
        <o:PixelsPerInch>96</o:PixelsPerInch>
        </o:OfficeDocumentSettings>
    </xml><![endif]-->

Format detection `meta` tags can be added depending on your style needs. These tags are used to prevent iOS clients from automatically styling certain elements that they recognize, such as phone numbers and dates, and turning them into links that direct the user to the phone or calendar app. If you want to turn off that functionality, include the appropriate tag from below:

    <meta name="format-detection" content="telephone=no">
    <meta name="format-detection" content="date=no">

Some emails included a `robot` `meta` tag that is used to instruct browsers not to index the page. These were all used in conjunction with OpenGraph. If you aren't using OpenGraph, don't worry about this tag. 

Some emails also included a `referrer` `meta` tag. This is used for SEO and analytics purposes and informs the browser who the referrer is. I need to do more digging on this one, but I have a feeling this only provides value when the email is viewed in browser or perhaps when a link is clicked. More research is needed. 

## Style

Only three things were looked at here. Whether the email included embedded CSS, whether it had media queries, and if there was an additional embedded css section specifically for Outlook.

23 of 25 emails included media queries. While you can create responsive emails without using media queries and instead using simple layouts and hybrid or 'spongy' coding, it seems like pretty much everyone is using media queries. Especially if you want your mobile email to render different than your desktop email, I've found @media queries to be much easier by adding mobile and/or desktop classes to change elements easily based on the screensize.

20 of 25 emails included embedded CSS. This means they included their CSS in a `<style>` tag in the `<head>` of their email. **Note:** This does not mean that they didn't also have styles inlined in their email. From a production standpoint, embedding your CSS is cleaner and more efficient than only inlining. In addition to embedded CSS, I recommend also inlining your emails using a CSS inliner. 

On par with what we've seen for these emails supporting Outlook, 9 of 25 emails had a separate embedded CSS section just for Outlook. Again, if you're targeting Outlook, this is a good idea.


## Body

This section will be written soon!
