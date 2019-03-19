# About Study

> study priod : Mar 2 ~

- [VueJS Homepage](https://vuejs.org)

I will read `vue.js` guide document and summarize what I need with my opinion.

## My background

- PHP: 3yrs+
- node.js: X
- MySQL: 3yrs+
- HTML, CSS, JS : 3.5yrs+
- Python: 1yrs+

## Goal of Study

- proficient at vue.js
- Understanding of front-end javascript framework
- experiencing rule-based source

# Set up environment

macOS 10.14.3  
Chrome 72-73

## IDE: [Visual Studio Code](https://code.visualstudio.com/)

- Plug-in
  - ESLint
  - HTML Snippets
  - Vue 2 Snippets
  - Debugger for Chrome
  - Prettier

### Set up ESLint

1. Install ESLint
   ```
   npm install -g eslint
   ```
2. Configure ESLint
   ```
   eslint --init
   ```
   ```bash
   ? How would you like to use ESLint? To check syntax, find problems, and enforce code style
   ? What type of modules does your project use? JavaScript modules (import/export)
   ? Which framework does your project use? Vue.js
   ? Where does your code run? Browser, Node
   ? How would you like to define a style for your project? Answer questions about your style
   ? What format do you want your config file to be in? JSON
   ? What style of indentation do you use? Tabs
   ? What quotes do you use for strings? Single
   ? What line endings do you use? Unix
   ? Do you require semicolons? Yes
   ```
3. Restart VSCode

4. Airbnb ESLint
    ```bash
    yarn add eslint-config-airbnb
    ```
    .eslintrc.json
    ```json
    ...
    "extends": [
        "airbnb-base",
        ...
    ],
    ...
    ```

### Set up Prettier
   ```json
    "[typescript]": {
        "editor.formatOnSave": true,
        "editor.formatOnPaste": true    
    },
    "[html]": {
        "editor.formatOnSave": true,
        "editor.formatOnPaste": true    
    },
    "[javascript]": {
        "editor.formatOnSave": true,
        "editor.formatOnPaste": true     
    }
   ```

## Brower: Chrome

- Plug-in
  - Vue.js devtools
