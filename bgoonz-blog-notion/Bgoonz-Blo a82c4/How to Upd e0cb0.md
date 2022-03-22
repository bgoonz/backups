# How to Update Multiple Web Pages Using JavaScript

[https://www.mediacollege.com/internet/javascript/page/update-multiple-pages.html](https://www.mediacollege.com/internet/javascript/page/update-multiple-pages.html)

Using JavaScript, you can create a separate file which contains content for your web page. To update all the pages simultaneously, simply update the JavaScript file.

**Pros:**

- Easy to implement.
- Does not rely on any special HTML extension or server configuration.

**Cons:**

- Relies on the user having JavaScript enabled.
- Updates are more tricky than other methods.

### Step 1: Create JavaScript File

Create a plain text document and name it with a .js extension, for example masterscript.js. Using the JavaScript [document.write method](https://www.mediacollege.com/internet/javascript/basic/document-write.html), enter the content you want to be displayed on every page like so:

document.write("<div style='color:blue; font-size:12pt;'>");
 document.write("© Copyright Myname 2004");
 document.write("</div>");

*Note:* You don't need to include script tags in this file.

### Step 2: Add JavaScript Code to Pages

On every page where you want the content to appear, insert the following code:

<script language="JavaScript" type="text/javascript" src="masterscript.js">
 </script>

To change the content on every page, edit the contents of the masterscript.js file.