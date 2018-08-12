# Setup



## Cloning
Type `git clone https://github.com/F-Tahir/HTML5Template.git foldername` to clone the project

## Getting packages via npm
This project uses `Node` packages to compile SCSS files into vanilla CSS. Make sure you have Node.js installed, and this will also install _npm_. `Node` packages are not checked in, and will have to be installed after cloning the project. After cloning, to install npm packages associated with this project, do the following:

1. Navigate into the cloned project on terminal (`cd path/to/proj`) 
2. Type `npm install`
3. This will install all dependencies listed in `package.json` into a folder called `node_modules`. This folder should **never be checked in**.
4. Edit `package.json` and `package-lock.json` (if it exists) to change the project name and description if required. Normally this wouldn't be done when working on a production project, but as this project is just a template, the default project name and description will need to be overridden.

## Version controlling the cloned project
Before version controlling, make sure the project is using the latest version of _normalize.css_ from here: https://necolas.github.io/normalize.css/. If the file needs updated, copy the contents of the file from GitHub and replace it with the contents in `scss/vendor/_normalize.scss`.

**NOTE:** Make sure that `node_modules` is NOT checked in. `package.json` and `package_lock.json` can be checked in. To make sure `node_modules` does not get checked in, ensure that a `.gitignore` exists, ignoring the `node_modules` folder.

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

1. Recommended to keep the `full-width-container` and `small/medium/large-wrapper` classes. The `wrapper` classes set the max-width to 1280px, 960px, or 768px depending on which one is used, and centers the content on the page, leaving left and right margins. `full-width-container` contains the `wrapper` classes so that full width background colors/gradients/padding etc can be applied. 
2. If a full width background color is needed, create a new class e.g. `bg-red { background-color: red; }` and apply it to the outer div with the `full-width-container` class, e.g. `<div class="full-width-container bg-red"></div>`. The containers **should not be changed**.
3. Once an Apple icon is generated, this will also need to be added in the head. Use a favicon generator to generate this for you (discussed below), as guidelines change when new devices are released.



## SCSS Files

### main.scss

This is the main SCSS file which contains imports for other partial SCSS files, including `vendor` stylesheets, `_helper` stylesheet and a `_variable` stylesheets. Because this is the main stylesheet and all other stylesheets are imported into this one, this is the only stylesheet which should need compiled into css.

To define any new rules, type them under the `User defined styles` section.

To create a new partial file to be imported into `main.scss`, prefix it with a `_` so that node-sass does not attempt to compile it into `css`. See the "Compiling main.scss" section for more information.

### _variables.scss (partial)
This is a partial which defines all variables used in `main.scss`, such as primary and tertiary colours, breakpoints and font sizes. This is included as an `import` in `main.scss` and does not need to be compiled separately.

### _helper.scss (partial)
This is a partial which defines a list of helper functions which can be used in the project, such as aligning text, removing padding/margin and hiding elements. This is included as an `import` in `main.scss` and does not need to be compiled separately.

If stylings are being applied often, they should probably be migrated to this file.

### Vendor files
Vendor files are third party stylesheets (such as normalize.css as used in this project). They should normally be imported into `main.scss` so that only one `css` file is generated. In order to import a third party stylesheet into `main.css`, it must be a partial. To make it a partial, prefix it with `_`. This will also mean that a `.css` file is not generated when compiling.

If third party stylesheets are in `*.css` format instead of `*.scss`, simply renaming them to `_*.scss` allows you to import them into `main.scss`, so do this if a third party stylesheet does not have a `.scss` format.

If the vendor file should not be a partial, then don't prefix it with `_`, and when compiling (see below), a `*.css` file will be generated, which can then be referenced in your html file.

### _normalize.scss
Optional, but highly recommended css files that allow various browsers to render elements consistently. Some browsers have bugs/inconsistencies that lead to incorrect rendering of an element and including this file fixes these issues. This is imported into `main.scss` in order to limit the number of HTTP requests.

**Not recommended**: If you wish to remove these files, also remove the `import` from `main.scss`.

#### Compiling SCSS files
A script has been set up to compile any non-partial `scss` files automatically.

Simply run `npm run watch:scss` in a terminal and any scss files in the `scss/` folder will be watched.  Whenever any changes are made to this folder (partial or non-partial files), the `watch:scss` script will automatically compile `scss` files to `css` format and output to the `css/` folder by running the `npm run compile:scss` script also in `package.json`. 

The `compile:scss` script compiles any **non-partial** `*.scss` files in the `scss` folder into `*.css` and saves them to the `css` folder, using the same name. E.g. `scss/main.scss` will be compiled as `css/main.css`.  Hence, if `normalize.scss` (without a `_`) was saved in the `scss` folder and the `watch:scss` script was running, a `normalize.css` file would also be generated because `normalize.scss` was not saved as a partial. **So make sure you prefix all partials with `_` or `.css` versions will be generated.**

In order to stop watching, stop running the command on your terminal (normally `Ctrl+C` on Windows/Linux and `Cmd+C` on Mac). 

## Javascript files

### 'vendor' folder

All 3rd party plugins (e.g. jQuery, Select2, Modernizr.js) should go in to this folder.

## npm files

Checked in are 2 files related to `npm`: `package.json` and `package_lock.json`. `node_modules` is also associated with `npm`, but should NEVER be checked in, instead to generate the `node_modules` folder, `npm init` should be typed into the terminal and this wil install all the dependencies listed in `package.json`.

### package.json
This file:
* lists all the packages that the project depends on. By default, it should only depend on `node-sass` which is installed as a developer dependency, not a production dependecy;
    * the packages are split up into **dev dependencies** and **production dependencies**. 
    * **dev dependencies** are modules that shouldn't go into production code, e.g. SCSS compilers, TypeScript compilers, build tools, and script runners.
    * **production dependencies** are modules that the website depends on and wouldn't function without.
    * To install dev dependencies, type `npm install -D package-name`. To install production dependencies, type `npm install package-name`.
    * To install 
* allows you to specify versions of the package that the project can use;
* stores information about your project (i.e. description, author, version).

This file **should** be checked into version control. When somebody is cloning your project, in order to also obtain the modules that the project relies on, they will need to type `npm install` to generate the `node_modules` folder.

### package-lock.json

This file describes the exact tree that was generated when a package was installed. This is so that subsequent installations of modules can generate identical trees, meaning that dependency issues will not be encountered.

The file is intended to be committed into repositories alomg with `package.json`.

### node_modules

This folder contains all the dependencies of the project, as listed in `package.json`. 

However, it **should not** be checked into version control. In order to generate this folder when cloning a repository, the user must type `npm install` which will create this folder and install all the dependencies that are listed in `package.json`. This is the first thing that should be done when cloning a repository.

#### main.js file

This file should include any custom JS that is common to all pages, i.e. opening and closing a privacy policy modal.

#### Other files

For sizeable chunks of JavaScript that are only used on a certain page, a new .js file should be created.

## .htaccess

File used to configure a server. Most standard configuration should already be done and this file should not need to be edited.

## humans.txt
_This file is optional._ humans.txt is an initiative for who built the website. Read more at http://humanstxt.org/. 

## robots.txt
_This file is optional._ Web crawlers often traverse the web in order to index web content (i.e. Google) or to scan for email addresses (spammers often do this). This file allows you to define rules that specify which pages should not be searched. Note that you **should not** include any hidden information as this page is publicly accessible at http://<yourdomain>/robots.txt


# Favicon Generators

The boilerplate code only includes a standard 16x16 favicon icon and will not support Windows tiles or Apple touch icons. This is because standards are always changing and a favicon generator should be used for each project. A favicon generator requires a 260x260 file and is then downsampled to relevant sizes without losing quality.

See https://realfavicongenerator.net/. 

## Notes
1. When using this tool, a site.webmanifest file will be generated. This is required by Chrome so that the "Add to Home Screen" prompt shows up where users can pin tiles. In this file, the `name` and `short_name` values are left blank. Be sure to fill this out. This is referenced on your page by the `<link rel="manifest" href="/site.webmanifest">` line generated by the above website, so be sure to include this in the `head` tag of all pages.
2. Make sure that when creating a new html file, all `<link>` tags are copied to this new file so that each page has a favicon, Apple touch icon and so on.
3. The `browserconfig.xml` file is used for the Windows 10 start menu tiles. If you wish to change the tile's colour, open the file and edit the `<TileColor>` tag. The `<meta name="msapplication-TileColor>` content will also need to be changed in all html file `<head>` tags.
4. The `<meta name="theme-color" content="#ffffff">` line generated by the website sets the color of the address bar on Chrome for Android, for Lollipop and above. `#ffffff` is default, but this can be changed by changing that value.
5. _optional_ If you wish to generate Open Graph metadata for Facebook, use https://realfavicongenerator.net/social/. This allows you to design the appearance of your pages when shown in Facebook (i.e. Timeline posts). If this is not used, Facebook will decide the content for you.
