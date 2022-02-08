# 1002-miniprojects
Starting Template for CSS Tailwinds

Before you do anything, first create a Git repository:
git init

Then you create a .gitignore file and open it in the editor There you insert:
  node_modules


In the terminal you execute the following 3 commands:
  npm init -y
    > This creates the package.json file
    
  npm install tailwindcss postcss postcss-cli autoprefixer
    Attention: The postcss-cli is not mentioned in the official documentation. But we need it! (see below)
    
  npx tailwindcss init -p
    ● This creates the tailwind.config.js (The file is important, otherwise autocomplete will not work in VS Code)
    ● The -p ensures that the postcss.config.js file is created at the same time.
    
  copy this to tailwind.config.js
  module.exports = {
    content: ["./dist/**/*.{html,js}"],
       theme: {
        extend: {},
       },
      plugins: [
        ],
     }
    
    
    
Create folder structure and files:
  ● tailwind.css
  ● Folder “dist/css” (everything goes together in VSC!)
    > The code for publishing is then in the “dist” folder
  ● A file “styles.css” in the css folder
  ● A file index.html in /dist/
  ● In the index.html with “! + TAB”create an HTML frame
  
Copy the 3 lines into tailwind.css:
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
  
In the /dist/index.html
  <link rel="stylesheet" href="css/styles.css">
  
In the /package.json
  "scripts": {
    "build": "postcss tailwind.css -o dist/css/styles.css",
    "watch": "postcss tailwind.css -o dist/css/styles.css --watch"
  },

Note: These scripts only work with the “postcss-cli”. That is the reason why we installed this
before - different from the official Tailwindcss documentation!
(CLI = Comand Line Interface)

In the terminal you now run either npm run build or npm run watch to fill your styles.css with Tailwind styles. The difference is that npm run build is a one-time compilation, while npm run watch “waits” for changes in the background. The result is a /dist/styles.css with all the tailwind.css styles


In index.html we can now give the body a background color:
  <body class="bg-blue-400">
Then we open the page with the live server (right-click in the index.html) Then we should see a blue page!

- Install tailwindcss-debug-screens
    npm install tailwindcss-debug-screens --save-dev
