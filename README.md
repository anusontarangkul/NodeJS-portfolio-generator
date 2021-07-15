# Portfolio Generator

A command line interface app in Node that allows you to generate a portfolio. The user is prompted questions about their github profile and projects. This data is returned as an index.html file and CSS styling is applied to it.

![Demo-terminal](./demo-terminal.png)

![Demo-index](./demo-index.png)

|                                         |                                                               |                                                   |
| :-------------------------------------: | :-----------------------------------------------------------: | :-----------------------------------------------: |
|  [Introduction](#portfolio-generator)   |            [Table of Contents](#table-of-contents)            | [Development Highlights](#development-highlights) |
|         [Deployment](#deployed)         | [Description of Page Building](#Description-of-Page-Building) |       [Code Hightlights](#code-highlights)        |
| [Technologies Used](#Technologies-Used) |                      [Credits](#Credits)                      |                [License](#License)                |

## Development Highlight

- Use Node.JS file system modules (copyFile, writeFile)
- Use Inquirer.JS from npm
- Object destructuring
- Asynchronous functionality with JavaScript Promise objects

## Deployment

Install dependencies.

```
npm i
```

Run the app.

```
node app.js
```

## Description of Page Building

### Organization

- dist
- src
- utils
- .gitignore
- app.js
- LICENSE
- package-lock.json
- package.json
- README.md
- demo

### Description

- The generated html file and copied css file are created in the `dist` folder.
- Create the template literal functions and original css file in `src` folder.
- The utils has the promise to create the index.html and style.css files.
- The app.js holds the inquirer prompts and callback function to the utils generate site function.

## Code Highlights

Creating a file in node using the file system. A promise is used for asynchronous functionality.

```JavaScript
const writeFile = fileContent => {
    return new Promise((resolve, reject) => {
        fs.writeFile('./dist/index.html', fileContent, err => {
            if (err) {
                reject(err);
                return;
            }
            resolve({
                ok: true,
                message: 'file created!'
            });
        });
    });
};
```

After the user is prompted with questions, we have a chained asynchronous function to generate the file and catch errors. This style was used to avoid too many callbacks.

```JavaScript
promptUser()
    .then(promptProject)
    .then(portfolioData => {
        return generatePage(portfolioData);
    })
    .then(pageHTML => {
        return writeFile(pageHTML);
    })
    .then(writeFileResponse => {
        console.log(writeFileResponse);
        return copyFile();
    })
    .then(copyFileResponse => {
        console.log(copyFileResponse)
    })
    .catch(err => {
        console.log(err)
    });
```

## Technologies Used

### Frontend Languages

- [HTML](https://www.w3schools.com/html/)
- [JavaScript](https://www.javascript.com/)
- [CSS](https://www.w3schools.com/css/)

### Backend Languages

- [Node.js](https://nodejs.org/en/)

### NPM Dependencies

- [Inquirer.js](https://www.npmjs.com/package/inquirer)

## Credits

|                           |                                                                                                                                                                                                       |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **David Anusontarangkul** | [![Linkedin](https://i.stack.imgur.com/gVE0j.png) LinkedIn](https://www.linkedin.com/in/anusontarangkul/) [![GitHub](https://i.stack.imgur.com/tskMh.png) GitHub](https://github.com/anusontarangkul) |

## License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
