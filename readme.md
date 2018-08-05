# Setup

## Cloning
Type `git clone https://github.com/F-Tahir/HTML5Template.git` to clone the project

## Version controlling the cloned project
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

Note that once an Apple icon is generated, this will also need to be added in the head. Use a favicon generator to generate this for you (recommended), as guidelines change when new devices are released.

## main.css
Contains styling for older browsers, as well as common helpers for screenreaders/element visibility. This file should not need to be edited and styling can be added under the `User Defined Styles` section.

## normalize.css/normalize.min.css
Optional, but recommended css files that allow various browsers to render elements consistently. Some browsers have bugs/inconsistencies that lead to incorrect rendering of an element and including this file fixes these issues. 

**Not recommended**: If you wish to remove these files, also remove the stylesheet reference in `index.html`'s `header` tag

## humans.txt
humans.txt is an initiative for who built the website. Read more at http://humanstxt.org/. This file is optional.

## robots.txt
Web crawlers often traverse the web in order to index web content (i.e. Google) or to scan for email addresses (spammers often do this). This file allows you to define rules that specify which pages should not be searched. Note that you **should not** include any hidden information as this page is publicly accessible at http://<yourdomain>/robots.txt


## Javascript files

### 'vendor' folder

All 3rd party plugins (e.g. jQuery, Select2, Modernizr.js) should go in to this folder.

#### main.js file

This file should include any custom JS that is common to all pages, i.e. opening and closing a privacy policy modal.

## .htaccess

File used to configure a server. Most standard configuration should already be done and this file should not need to be edited.


# Favicon Generators

The boilerplate code only includes a standard 16x16 favicon icon and will not support Windows tiles or Apple touch icons. This is because standards are always changing and a favicon generator should be used for each project. A favicon generator requires a 260x260 file and is then downsampled to relevant sizes without losing quality.

See https://realfavicongenerator.net/. 

## Notes
1. When using this tool, a site.webmanifest file will be generated. This is required by Chrome so that the "Add to Home Screen" prompt shows up where users can pin tiles. In this file, the `name` and `short_name` values are left blank. Be sure to fill this out.
2. The `browserconfig.xml` file is used for the Windows 10 start menu tiles. If you wish to change the tile's colour, open the file and edit the `<TileColor>` tag.