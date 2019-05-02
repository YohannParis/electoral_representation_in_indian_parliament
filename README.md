# Brookings Interactive Template

Version 3.1
Last update: 2019 May 01

### Authors
Eric Abalahin <<eabalahin@brookings.edu>>
Yohann Paris <<yparis@brookings.edu>>


### Usage
This document outlines the process and requirements for submitting an interactive for use on Brookings.edu.

## Process
All design and code must be reviewed and approved by the Office of Communications before it will be allowed on Brookings.edu. Code must be submitted in the format described below; if it is not, we will ask you to resubmit the code in the proper format before it can be reviewed and approved.

If you are considering any kind of interactive, we recommend that you contact the appropriate Communications Advisor as far in advance as possible. You must inform them about the interactive no fewer than ten business days before the desired publication date.

Once you have contacted the Communications Advisor, they will coordinate review by the web and design teams in the Office of Communications.

After any necessary changes have been made and the interactive approved, the final code should be submitted to the Office of Communications. The Office of Communications will be responsible for loading the code onto the website, and will provide the information necessary to publish the associated piece of content live.

# Structure
The files should be sent in a folder using the name of the interactive. The folder name should be lowercase, with all words separated by dashes.
Example: `immigration-by-the-numbers`, or `fdip-2017`.

The folder should use the following structure:
```bash
name-of-the-interactive
    ├─ index.html
    ├─ app.css
    ├─ app.js
    ├─ assets
    ├─ source (optional)
    └─ vendor (optional)
```

The final code to be displayed on brookings.edu must be separated into three files, even if some may be empty:
- ALL HTML: `index.html`
- ALL CSS: `app.css`
- ALL JavaScript: `app.js`

It is IMPORTANT to note that all of your code should be in those three files, and that any code within the optional folders are solely for review/archiving purposes.

# index.html
The HTML is meant to be integrated into a brookings.edu webpage, and be part of it; therefore, it should not contain any of the following tags": `<html>, <head>, <body>, <link>, <script>`.

Because of restriction imposed by Wordpress, no `<input>` tag can be used. Please create all your form elements in Javascript.

A best practice is to encapsulate all of your HTML inside a div tag with a unique id that you can reference in your CSS and JavaScript, in order to avoid conflict with brookings.edu’s own CSS and JavaScript: `<div id="name-of-interactive">[YOUR HTML HERE]</div>`

# app.js
Insert all your vendors code at the beginning of your file.

To make sure your JavaScript is self-contained and will not conflict with brookings.edu variables and scripts, encapsulate your JavaScript inside a self-contained function and load when the window event is ready.

Example:
```javascript
// YOUR VENDORS HERE

(function() {
    function app() {
        // YOUR CODE HERE
    }

    // Start the interactive when the DOM is ready
    document.addEventListener('readystatechange', function() {
        document.readyState === 'complete' && app();
    }, false);
})();
```

No AJAX call shall be made from outside brookings.edu, or on the CDN with your code. The URLs to access your data in the assets folder via AJAX is in the following format:
`https://c24215cec6c97b637db6-9c0895f07c3474f6636f95b6bf3db172.ssl.cf1.rackcdn.com/interactives/[year-of-publication]/[name-of-the-interactive]/[name-of-file]`

Example:
`https://c24215cec6c97b637db6-9c0895f07c3474f6636f95b6bf3db172.ssl.cf1.rackcdn.com/interactives/2017/the-wall/app.css`

Those files can be minified and/or uglified ONLY if the original code is provided. Those files should be put in a folder named source. This folder is only intended to facilitate the review process. All JavaScript code should be in `app.js`. All CSS code should be in `app.css`.

```bash
name-of-the-interactive
    [..]
    └─ source
            ├─ main.less
            ├─ reset.less
            └─ dev.js
```

# assets
Data and media files, e.g. images, audio/video or PDFs, used by the interactive must be placed in a folder named assets. This is where you will store your data that is access via AJAX.

```bash
name-of-the-interactive
    [..]
    └─ assets
            ├─ logo.png
            ├─ image.svg
            └─ data.csv
```

All files can be accessed with the following URL:
`https://c24215cec6c97b637db6-9c0895f07c3474f6636f95b6bf3db172.ssl.cf1.rackcdn.com/interactives/[year-of-publication]/[name-of-the-interactive]/assets/[name-of-file]`

# vendors
The vendors folder should contain all libraries and/or frameworks needed to run the interactive. This includes any files from third-party vendors.

This folder is only intended to help the review process. All JavaScript code should also be in `app.js`.

```bash
name-of-the-interactive
    [..]
    └─ vendor
            ├─ bootstrap.css
            ├─ d3.js
            └─ normalizr.js
```

Before using third-party code, please contact the authors of this document to get approval. All third-party code must be reviewed by the Office of Communications, and all usage agreements for any libraries, including open source, must be reviewed by the Office of the General Counsel.