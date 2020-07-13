# Resources

In addition to the resources that are linked throughout this repo, I wanted a page for quick reference to common HTML email development resources. 
There are plenty of great resources out there to help you in your HTML email development journey. Below are some that I have found most useful.

###The Basics

These resources are great for getting a handle on the basics of HTML email development.

- [Email Design Reference](https://templates.mailchimp.com/development/html/) by Mailchimp
- [Build an HTML Email Template from Scratch](https://webdesign.tutsplus.com/articles/build-an-html-email-template-from-scratch--webdesign-12770) from TutsPlus
- [Which Code Should I Include in Every Email?](https://www.emailonacid.com/blog/article/email-development/which-code-should-i-include-in-every-email/) by Email on Acid
- [Foundation: Email Coding 101](https://litmus.com/community/learning/13-foundations-email-coding-101) by Litmus


### Deep Dive

Similar to the above list, but goes more in depth and builds on your initial knowledge of HTML email development to gain a deeper understanding.

- [Coding your HTML Email for Any Device](https://www.campaignmonitor.com/dev-resources/guides/coding-html-emails/) by Campaign Monitor
- [Ask a Designer: Tables or Divs for Email](https://www.campaignmonitor.com/blog/email-marketing/2019/04/ask-a-designer-tables-or-divs-for-email/#:~:text=Proper%20coding%20is%20really%20important,design%20issues%2C%20including%20padding%20problems.) by Campaign Monitor


### Issue-Specific

These resources help with common, specific HTML email development challenges. 

- [Using Ghost Columns to Fix Alignment Problems in Outlook](https://www.emailonacid.com/blog/article/email-development/using-ghost-columns-to-fix-alignment-problems-in-outlook/) by Email on Acid
- [CSS Support Guide](https://www.campaignmonitor.com/css/) by Campaign Monitor ***This is an excellent resource. Easily find out if a specific CSS attribute will render properly in an email client.
- [Outlook Conditional CSS](https://stackoverflow.design/email/base/mso/) by Stack Overflow
- [Get Started: Gmail Promotions Tab](https://developers.google.com/gmail/promotab/overview) by Google

### Tools

The following tools can help you optimize your HTML email coding.

#### CSS Inliners

CSS Inliners help to streamline production. Instead of inlining an entire email by hand, you can embed your CSS in `<style>` tags in the `<head>` of your document and these tools will apply them to the correct elements in the body of your email. 

- [Responsive Email CSS Inliner](https://htmlemail.io/inline/) by HTMLemail.io  
- [Premailer](https://www.mrtemplates.com/premailer/) by Alex Dunae

#### Diff Tool

If you're using an IDE such as VSCode or Atom, this is already built in. For those that are not, however, a Diff tool helps you compare two pieces of code to quickly and easily find differences between them. Use this to debug why two similar sections of your HTML email are rendering differently.

- [Diffchecker](https://www.diffchecker.com/) by Diffchecker

#### Gmail Promotions Tab Builders

Gmail's promotions tab allows for additional features to be represented on your emails including logo, featured image, and promo deals. They are included via a `<script>` tag in the `<head>` of your document or via Microdata in the `<body>` of your document.

- [Gmail Promotion Tab Markup Tool](https://freshinbox.com/tools/gmailpromotab/) by Fresh Inbox
- [Gmail Promotions Builder](https://litmus.com/community/gmail-promotions-builder) by Litmus

