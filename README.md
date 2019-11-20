# Getting started


## Table of Contents

- Windows
  - [Visual Studio Code](#Getting-Started-with-Visual-Studio-Code-on-Windows)
- Ubuntu
  - [Add to a project in Visual Studio Code](#Add-elm-to-an-existing-npm-project-in-VS-Code)


## Windows


### Getting Started with Visual Studio Code on Windows

1. Download and install [Visual Studio Code](https://code.visualstudio.com/)
1. Download and install [Nodejs](https://nodejs.org/en/)
1. Launch Visual Studio Code
1. From the menu bar, chose File, Preferences, Extensions
1. Install the extension “ElmLS”
1. From the menu bar, chose File, Preferences, Settings
1. Within Settings, navigate to Extensions, Elm configuration
1. Change the settings of “Compiler” to `.\\node_modules\\.bin\\elm` and change the settings of “Format Command” to `.\\node_modules\\.bin\\elm-format`
1. From the menu bar chose File, Open Folder
1. Inside Documents, create a folder MyFirstElmProject and open it
1. From the menu bar, chose Terminal, New Terminal
1. Inside the terminal, enter and execute the command `npm install --save-dev elm elm-format`
1. Inside the terminal, enter and execute the command `npx elm init`, and confirm with entering `Y<Enter>`
1. From the menu bar, chose File, New File
1. From the menu bar, chose File, Save File and save the file as `src/Main.elm`
1. Enter the following source code in that file:
   ```elm
   module Main exposing (..)

   import Html exposing (text)

   main = text "Hello world!"
   ```
1. Auto-format the source code using the keyboard shortcut `Shift-Alt-F`
1. From the menu bar chose File, Save
1. Compile your example program using the keyboard shortcut `Ctrl+F5`
1. From the menu bar, chose File, New File
1. From the menu bar, chose File, Save File and save the file as `index.html`
1. Enter the following source code in that file:
   ```html
   <!doctype html>
   <html>
     <head>
       <meta charset="utf-8">
       <title>My First Elm Project</title>
     </head>
     <body>
       <script src="elm.js"></script>
       <script>
         Elm.Main.init({ node: document.querySelector("main") });
       </script>
       <main></main>
     </body>
   </html>
   ```
1. Open the file `index.html` with your browser


## Ubuntu


### Add elm to an existing npm project in VS Code
Elm can be added very easily to an existing project, which uses npm as a package manager. 

1. Install elm via npm locally:
    ```bash
    npm install --save-dev elm elm-format
    ```
2. Install the VS Code extension *elm: Elm Language Support for Visual Studio Code*
3. Initialize elm with 
    ```bash
    npx elm init
    ```
    It will ask, if it should create the file *elm.json*. Confirm with "Y". The file *elm.json* contains some basic dependencies.

    `npx` is a small wrapper, that lets you execute command line tools, which are in the folder *node_modules*, but are not in available in the terminal.
4. Configure the elm extension. The elm extension assumes, that elm is available globally in the command line, which it is not in this approach. Therefore, the location of the compiler has to be configured.
    1. Open settings with `Ctrl+,` or under File > Settings > Settings
    2. Search for "elm compiler".
    3. Enter "./node\_modules/.bin/elm" as command.
    4. Search for "elm format".
    5. Enter "./node\_modules/.bin/elm-format" as command.
5. Add the folder *elm-stuff* to .gitignore. It is a temp folder for the elm compiler.
6. Create a hello world file *src/Main.elm* with the following content.
    ```elm
    module Main exposing (..)

    import Html exposing (text)

    main = text "Hello there!"
    ```
7. Try auto format by pressing `Ctrl+Shirt+i`. If you are not sure about the shortcut, you can look it up by pressing `Ctrl+p`. Then type "\>format".
8. Compile with `npx elm make src/Main.elm`. That will create the files *elm.js* and *index.html*.

    To embed the resulting JavaScript code on an existing page, run 
    ```bash
    npx elm make src/Main.elm --output=dist/js/elm.js
    ```
    You can also add a script to the *package.json* from npm:
    ```json
    {
        "script": {
            "build-elm": "elm make ./src/Main.elm --output=dist/js/elm.js"
        }
    }
    ```
    In the npm scripts there is no need to use `npx`.
9. To include the result in an existing html file, add the following:
    ```html
    <div id="elmApp"></div>
    <script src="js/elm.js"></script>
    <script>
        const elmApp = Elm.Main.init({
            node: document.getElementById("elmApp")
        });
    </script>
    ```
    This will replace the div element with the elm application, in our case the div will be replaced by the plain text "Hello there!".
10. Now open the html file by whatever means your project provides.
