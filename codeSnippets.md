# Code snippets

This file contains a collection of code snippets, categorized by usage, ex. images, tables, templates.

## Mobile-stacking multi-column layouts

This section details multi-column layouts (2+ columns) that stack on mobile. These can be tricky, so use these templates to help guide you.

### Basic 2-column set layout

Here's the CSS for this layout: 

    <!--
    Must use the following styles in the mobile stylesheet with this block:
    THIS RESETS THE BORDER-SPACING TO 0 ON MOBILE. WITHOUT THIS, THERE'S TOO MUCH PADDING
    .ltr-outer-table {
    border-spacing: 0px;
    }
    THIS ENABLES EACH CELL TO BECOME FULL WIDTH AND STACK VERTICALLY
    .mobile-column-outer {
      display: block !important;
      width: 100% !important;
    }
    ADDS PADDING TO THE CELL THAT BECOMES THE TOP BLOCK ON MOBILE
    .mobile-top-block {
     padding-bottom: 10px !important;
    }
    ADDS EQUAL TOP AND BOTTOM PADDING FOR ALL MIDDLE BLOCKS ON MOBILE
    .mobile-middle-block {
     padding-top: 10px !important;
     padding-bottom: 10px !important;
    }
    ADDS BOTTOM PADDING ON THE FINAL/BOTTOM BLOCK ON MOBILE
    .mobile-bottom-block {
     padding-top: 10px !important;
    }
    THIS RESETS THE CELL
    .mobile-column-inner {
      padding: 10px !important;
    }

    NOTES: MUST USE TH INSTEAD OF TD FOR LTR COLUMNS.
    -->
    
    
 And here's the html for the layout
 
 
     <!-- left to right table 1--> 
    <table cellpadding="0" cellspacing="16" border="0" width="100%" bgcolor="#ffffff" class="bloc-main" style="background: #ffffff;direction: ltr;  border: 0px solid #ffffff; border-collapse: separate !important;" dir="ltr">
      <tr>
       <th class="mobile-column-outer mobile-top-block" width="50%" dir="ltr">
     
     <!--Ghost Table for Column 1-->
      <!--[if mso]>
    <table role="presentation" align="center" border="0" cellspacing="0" cellpadding="0" width="210">
    <tr>
    <th align="center" valign="middle" width="210"><[endif]-->
          <table cellpadding="0" cellspacing="0" border="0" width="100%" align="center">
            <tr>
              <td class="mobile-column-inner" style="padding: 8px; height: 100%; align: center;" align="center" valign="middle">
                INSERT COLUMN 1 / TOP BLOCK CONTENT HERE
              </td>
            </tr>
          </table>
      <!--[if mso]>  
    </th>
    </tr>
    </table><[endif]-->
      <!--End Ghost Table for Column 1-->
     
    </th>
    <th class="mobile-column-outer mobile-middle-block" width="50%" dir="ltr">
     
    <!--Ghost table for Column 2-->
      <!--[if mso]>
    <table border="0" align="center" cellspacing="0" cellpadding="0" width="210">
    <tr>
    <td align="center" valign="middle" width="210"><[endif]-->
          <table cellpadding="0" cellspacing="0" border="0" width="100%" align="center">
            <tr>
              <td class="mobile-column-inner" style="padding: 8px; height: 100%;" align="center" valign="middle">
                INSERT COLUMN 2 / BOTTOM BLOCK CONTENT HERE
              </td>
            </tr>
          </table>
      <!--[if mso]>
    </td>
    </tr>
    </table>
    <[endif]-->
      <!--End ghost table for Column 2-->
     
    </th>
    
      </tr>
    </table>
<!--End LTR Table for 2 columns-->


And here's the code for a 3 column table:

    <!--Insert LTR table for 3 columns-->
    <!-- left to right table 1--> 
    <table cellpadding="0" cellspacing="16" border="0" width="100%" bgcolor="#ffffff" class="bloc-main ltr-outer-table" style="background: #ffffff;direction: ltr;  border: 0px solid #ffffff; border-collapse: separate !important;" dir="ltr">
      <tr>
       <th class="mobile-column-outer mobile-top-block" width="33.3%" dir="ltr">

         <!--Ghost Table for Column 1-->
          <!--[if mso]>
    <table role="presentation" align="center" border="0" cellspacing="0" cellpadding="0" width="140">
    <tr>
    <th align="center" valign="middle" width="140"><[endif]-->
          <table cellpadding="0" cellspacing="0" border="0" width="100%" align="center">
            <tr>
              <td class="mobile-column-inner" style="padding: 8px; height: 100%; align: center;" align="center" valign="middle">
                <div data-type="slot" data-key="fjwbyicjba" data-label="Drop Column 1 here"></div>
              </td>
            </tr>
          </table>
          <!--[if mso]>  
    </th>
    </tr>
    </table><[endif]-->
          <!--End Ghost Table for Column 1-->

        </th>
        <th class="mobile-column-outer mobile-middle-block" width="33.3%" dir="ltr">

        <!--Ghost table for Column 2-->
          <!--[if mso]>
    <table border="0" align="center" cellspacing="0" cellpadding="0" width="140">
    <tr>
    <td align="center" valign="middle" width="140"><[endif]-->
          <table cellpadding="0" cellspacing="0" border="0" width="100%" align="center">
            <tr>
              <td class="mobile-column-inner" style="padding: 8px; height: 100%;" align="center" valign="middle">
                 <div data-type="slot" data-key="arfj8bswni" data-label="Drop Column 2 here"></div>
              </td>
            </tr>
          </table>
          <!--[if mso]>
    </td>
    </tr>
    </table>
    <[endif]-->
          <!--End ghost table for Column 2-->

        </th>
        <th class="mobile-column-outer mobile-bottom-block" width="33.3%" dir="ltr">

         <!--Ghost Table for Column 3-->
          <!--[if mso]>
    <table role="presentation" align="center" border="0" cellspacing="0" cellpadding="0" width="140">
    <tr>
    <th align="center" valign="middle" width="140"><[endif]-->
          <table cellpadding="0" cellspacing="0" border="0" width="100%" align="center">
            <tr>
              <td class="mobile-column-inner" style="padding: 8px; height: 100%;" align="center" valign="middle">
                 <div data-type="slot" data-key="aprnbuakqjeba" data-label="Drop Column 3 here"></div>
              </td>
            </tr>
          </table>
          <!--[if mso]>  
    </th>
    </tr>
    </table><[endif]-->
          <!--End Ghost Table for Column 3-->

        </th>
      </tr>
    </table>
    <!--End LTR Table for 3 columns-->
    
    
    
  ## Images
  
### Full-width mobile images, with Outlook fix

This fix is for when you have use images in a multi-column setup, as in the code above. On desktop, you want the images to be smaller so they fit in the column nicely, but then expand to fill a single column on mobile. To do this without stretching the image, you need a large image size. The issue with a large image size is that Outlook likes to ignore your width settings and display images based on what size they are. This fix creates an Outlook-only image and sets the `display` of the standard image to `none`, allowing you to have an image that renders well on desktop, mobile, and Outlook. The article that helped me find this solution can be found [here](https://jasemiller.medium.com/a-fix-for-outlook-image-issues-in-html-email-campaigns-b8dd1c8f7d16)


Here's the code: 

     <!--[if mso]>
          <table width="50%"><tr><td><img width="210" src="https://via.placeholder.com/600x400" alt="image" style="text-align: right; width: 210px; border: 0; text-decoration:none; vertical-align: baseline;"></td></tr></table>
          <div style="display:none">
       <![endif]-->
            <img src="https://via.placeholder.com/600x400" alt="" style="display: block; padding: 0px; text-align: center; height: auto; width: 100%; border: 0px none transparent;" width="600">
      <!--[if mso]>
          </div>
       <![endif]-->
