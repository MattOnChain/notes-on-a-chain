# mdBook

[mdBook](https://rust-lang.github.io/mdBook/index.html) was used to create this document. It is a command line tool to create books with Markdown. Markdown a simple way to format text that looks great on any device. It doesn’t do anything fancy like change the font size, color, or type - just the essentials to keep it nice and clean. If you don't like mdBook, you may consider [GitBook](https://www.gitbook.com) as a preferable alternative.

## Install mBook

1. Create a new folder like \LocalUserName\mdBook
2. Download the appropriate executable binary from [GitHub](https://github.com/rust-lang/mdBook/releases)
3. Unpack the file and move mdBook to the directory created above
  > mdBook is a CLI tool and therefore all actions are done in Terminal Mode
4. Add the mdBook folder to the PATH variable
```
nano ~/.zshrc
```
5. Add the following entry to the zshrc file
```
#Adding mdBook to PATH
export PATH=$PATH:~/mdBook
```
6. Save and exit: CTRL-X, Y, Enter
7. Restart zshrc
```
source ~/.zshrc
```
8. Verify the change was made
```
echo $PATH
```
## Create a Book

1. Initialize the new book
```
mdbook init your-book-title
```
2. Do you want a .gitignore to be created = y
3. Your mdBook is now located in your home folder

## Editing the Book with Visual Studio Code

Visual Studio Code (or VS Code) is a source code editor. In this case, it is a simple and effective tool for editing the .md Markdown files that are the source files from which the final HTML book will be rendered. In other words, you will write your content in VS Code.

1. Download [Visual Studio Code](https://code.visualstudio.com/docs/setup/mac) and move it to your Applications folder
2. In VS Code, install required extensions
   1. Settings > Extensions > Markdown All in One > Install
   2. Settings > Extensions > Code Spell Check > Install
3. In Visual Studio Code, open the book folder and desired .md file
   1. Bottom right, toggle HTML to Markdown for editing .md files
   2. Top right, click Open Preview on the Side
4. Make edits and save files as needed 

## mdBook Components

The mdBook folder is comprised of two main components
- The 'book' folder contains the rendered book in the form of CSS and HTML files. These are the files used by readers as they view the contents.
- The 'src' folder contains the source .md files. These are the files that are created and edited to makeup the content of the book. The Summary.md file is the table of contents that includes reference to the other .md files, each representing a separate chapter in the book.

## Common Markdown 

> Reference: [CommonMark.org](https://commonmark.org/help/) provides a recap of basic Markdown features

## Render the Book

Book rendering is the process through which the source .md files are converted to HTML. This is done by starting the related service as shown below.  You can leave this service running in Terminal while editing the book, or you can start the service  periodically, when you desire new HTML output files.

```
cd /users/yourmacusername/your-book-title
mdbook serve --open
```
Use CTRL-C to stop the service at any time.

## GitHub

GitHub is a code repository that may be used to host your mdBook files, making them internet accessible. This allows you to configure a website to link to the book for viewing by visitors of the site.

GitHub has many other features that may be useful, for example, the Issues feature can be a simple way to record notes of any future edits that you would like to make to the book.

### Upload the mdBook Files to GitHub

1. Create a Repository named like your-book-title
2. Under Code, create a Deploy Branch to represent the production Branch. This will be where you will host the currently accessible version of the book
3. Copy your local 'book' folder to a temporary location and rename it 'docs'
4. In GitHub open the Deploy Branch and click to Add Files
5. Drag your local 'docs' folder to GirHub and Commit the changes
6. Configure GitHub pages to host your uploaded files
   1. From your main Repository page, click Settings
   2. On the left, under Code and Automation, click Pages
   3. On the settings on the right, make sure the Build and Deployment Source is set to Deploy from a branch
   4. Set the Branch to deploy /docs
7. As needed going forward, to update your hosted book, simply repeat the steps above to upload a new local 'docs' folder so as to overwrite the previous version

At this point you have configured the automated 'pages build and deployment' workflow that will run behind the scenes to update the hosted pages each time the 'docs' files are updated.

### Linking to Your Hosted mdBook from a Website

To access the mdBook as hosted on GitHub pages, link to your book's introduction file

> https://mattonchain.github.io/notes-on-a-chain/introduction.html







