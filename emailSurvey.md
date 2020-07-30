## Summer 2020 Email Survey

Additional details are being added frequently. Check back for more updates!

### Instructions

- Download [Excel email comparison](Email-Construction-Comparison.xlsx)
- Follow along below while reviewing the comparison

## Purpose

While this was a relatively small (25 emails) comparison, it was useful to help draw out common patterns in optimal HTML email design as well as discover new use-cases and falllbacks. The purpose was to compare many of the common or frequent elements of modern, visually-impactful HTML emails to discover what works, what others are using, and ultimately, to learn more about HTML email development. 

Let's dig in.

## Layout of Spreadsheet

Individual emails are laid out as columns, and the fields I am exploring are listed as rows. Totals are found in the last column and help to guide my overall discoveries.

The fields are divided into 4 sections: Email basics, `HTML/Head`, `Style`, and `Body`. 

The email basics section includes a link to the email's code on [Really Good Emails](https://reallygoodemails.com/), the Email Service Provider used to send that email (if known), and if the email is marked as NOT being mobile-friendly by RGE. 

This spreadsheet gives you a good overview of patterns, but looking at the individual source code of individual emails is incredibly valuable. I suggest you use this file comparison as a guide, then solidify your understanding by digging into the source code of individual emails - including your own emails!

## HTML/Head

### DOCTYPE

Overall, the majority of emails(15 out of 25) used the xhtml 1.0 transitional DOCTYPE, which has long been a standard for HTML emails. 3 had no DOCTYPE declaration, which is inadvisable, 3 declared HTML5, 2 declared html 4.01 strict, 1 declared xhtml 1.0 strict and 1 declared html 4.01 loose. 

