# Setup

## Cloning
Type `git clone https://github.com/F-Tahir/HTML5Template.git` to clone the project

## Version controlling the cloned project
Before version controlling, make sure the project is using the latest version of _normalize.css_ from here: https://necolas.github.io/normalize.css/. All other files are custom and should not get outdated.

1. Navigate into the new project on terminal (`cd path/to/proj`)
2. Type `git init`
3. Add a new repository on GitHub/BitBucket
4. Type `git remote add origin https://github.com/user/repo.git`
5. Type `git add -A .` to track all files in the project 
6. Type `git commit -m "initial commit"
7. Finally, push to remote by typing `git push -u origin master`



# Files

## index.html
This file contains all the basic structure for a website with header (containing a navigation bar), a main and a footer section. The html language attribute has been set, as has the character set. A default favicon has been used. Note that no other icons (e.g. for Apple, Windows tiles and so on) have been generated. This is discussed below.

### Stubs to be filled in
1. Fill in the `<meta name="description" content="">` tag for SEO
2. Fill in the `title` tag
3. Remove everything between `<main>` tag as necessary.
4. Remove comments in HTML as necessary.

### Notes

1. Recommended to keep the `full-width-container` and `fixed-width-wrapper` class. `fixed-width-wrapper` sets the max-width to 1280px (can be edited) and centers the content on the page, leaving left and right margins. `full-width-container` wraps the `fixed-width` container so that full width background colors/gradients/padding etc can be applied. 
2. If a full width background color is needed, create a new class e.g. `bg-red { background-color: red; }` and apply it to the outer div with the `full-width-container` class, e.g. `<div class="full-width-container bg-red"></div>`. The containers **should not be changed** (except for the max-width property on the `fixed-width-wrapper` class)
3. Once an Apple icon is generated, this will also need to be added in the head. Use a favicon generator to generate this for you (discussed below), as guidelines change when new devices are released.

#### Wrapper vs Container
In programming languages the word **container** is generally used for structures that can contain more than one element.

A **wrapper** instead is something that wraps around a single object to provide more functionalities and interfaces to it.

Example:
```
<div class="container">
    <header class="wrapper">
        <h1>Title of page</h1>
    </header>
    <section class="wrapper">
        <p>Some text here</p>
    </section>
</div>
```


## main.css
Contains styling for older browsers, as well as common helpers for screenreaders/element visibility. The existing rules in the file should not need to be edited and new rules can be added under the `User Defined Styles` section.

## normalize.css/normalize.min.css
Optional, but highly recommended css files that allow various browsers to render elements consistently. Some browsers have bugs/inconsistencies that lead to incorrect rendering of an element and including this file fixes these issues. 

**Not recommended**: If you wish to remove these files, also remove the stylesheet reference in `index.html`'s `header` tag


## humans.txt
_This file is optional._ humans.txt is an initiative for who built the website. Read more at http://humanstxt.org/. 

## robots.txt
_This file is optional._ Web crawlers often traverse the web in order to index web content (i.e. Google) or to scan for email addresses (spammers often do this). This file allows you to define rules that specify which pages should not be searched. Note that you **should not** include any hidden information as this page is publicly accessible at http://<yourdomain>/robots.txt


## Javascript files

### 'vendor' folder

All 3rd party plugins (e.g. jQuery, Select2, Modernizr.js) should go in to this folder.

#### main.js file

This file should include any custom JS that is common to all pages, i.e. opening and closing a privacy policy modal.

#### Other files

For sizeable chunks of JavaScript that are only used on a certain page, a new .js file should be created.

## .htaccess

File used to configure a server. Most standard configuration should already be done and this file should not need to be edited.

# Favicon Generators

The boilerplate code only includes a standard 16x16 favicon icon and will not support Windows tiles or Apple touch icons. This is because standards are always changing and a favicon generator should be used for each project. A favicon generator requires a 260x260 file and is then downsampled to relevant sizes without losing quality.

See https://realfavicongenerator.net/. 

## Notes
1. When using this tool, a site.webmanifest file will be generated. This is required by Chrome so that the "Add to Home Screen" prompt shows up where users can pin tiles. In this file, the `name` and `short_name` values are left blank. Be sure to fill this out. This is referenced on your page by the `<link rel="manifest" href="/site.webmanifest">` line generated by the above website, so be sure to include this in the `head` tag of all pages.
2. Make sure that when creating a new html file, all `<link>` tags are copied to this new file so that each page has a favicon, Apple touch icon and so on.
3. The `browserconfig.xml` file is used for the Windows 10 start menu tiles. If you wish to change the tile's colour, open the file and edit the `<TileColor>` tag. The `<meta name="msapplication-TileColor>` content will also need to be changed in all html file `<head>` tags.
4. The `<meta name="theme-color" content="#ffffff">` line generated by the website sets the color of the address bar on Chrome for Android, for Lollipop and above. `#ffffff` is default, but this can be changed by changing that value.
<<<<<<< HEAD
5. _optional_ If you wish to generate Open Graph metadata for Facebook, use https://realfavicongenerator.net/social/. This allows you to design the appearance of your pages when shown in Facebook (i.e. Timeline posts). If this is not used, Facebook will decide the content for you.
=======
5. _optional_ If you wish to generate Open Graph metadata for Facebook, use https://realfavicongenerator.net/social/. This allows you to design the appearance of your pages when shown in Facebook (i.e. Timeline posts). If this is not used, Facebook will decide the content for you.
>>>>>>> 904a1ccb7993a7bc781ea3b88bb772a3eddfbeef
