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


## humans.txt
humans.txt is an initiative for who built the website. Read more at http://humanstxt.org/. This file is optional.

## robots.txt
Web crawlers often traverse the web in order to index web content (i.e. Google) or to scan for email addresses (spammers often do this). This file allows you to define rules that specify which pages should not be searched. Note that you **should not** include any hidden information as this page is publicly accessible at http://<yourdomain>/robots.txt


