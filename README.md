# Getting started

## Table of Contents

- Windows 10
  - [Visual Code](#Getting-Started-with-Visual-Studio-Code-on-Windows-10)


## Windows 10


### Getting Started with Visual Studio Code on Windows 10


1. Download and install [Visual Studio Code](https://code.visualstudio.com/)
1. Download and install [Nodejs](https://nodejs.org/en/)
1. Launch Visual Studio Code
1. From the menu bar, chose File, Preferences, Extensions
1. Search for “elm” and install the extension *elm: Elm Language Support for Visual Studio Code*
1. From the menu bar, chose File, Preferences, Settings
1. Within Settings, navigate to Extensions, Elm configuration
1. Change the settings of “Compiler” to `.\\node_modules\\.bin\\elm` and change the settings of “Format Command” to `.\\node_modules\\.bin\\elm-format`
1. From the menu bar chose File, Open Folder
1. Inside Documents, create a folder MyFirstElmProject and open it
1. From the menu bar, chose Terminal, New Terminal
1. Inside the terminal, enter and execute the command `npm install --save-dev elm elm-format`
1. Inside the terminal, enter and execute the command `.\\node_modules\\.bin\\elm init`, and confirm with entering `Y<Enter>`
1. From the menu bar, chose File, New File
1. From the menu bar, chose File, Save File and save the file as `Main.elm`
1. Enter the following source code in that file:
```elm
module Main exposing (..)

import Html exposing (text)

main = text "Hello world!"
```
1. Auto-format the source code using the keyboard shortcut `Shift-Alt-F`
1. From the menu bar chose File, Save
1. Compile your example program using the keyboard shortcut `Ctrl+F5`
1. Open the compiled file `index.html` with your browser
