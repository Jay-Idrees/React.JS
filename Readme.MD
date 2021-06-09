# React by Facebook

This readme file is my personal collection of basic infromation and tips about react from various sourees including the materials from the Columibia University software engineering course Udemy and my own experience. I have created this repository as a quick reference for myself, so I have only included the deescriptions that I would want to refer back to in the future. 

## React Packages

- `ReactDOM` takes the tree of components and renders them on the DOM. `npm install react-dom`
- `Bootstrap` will install bootstrap. `npm install --save bootstrap` and then import `import 'bootstrap/dist/css/bootstrap.min.css';` to the `index.js` file


## General points about React
- Uses JSX code which javascrpt code that looks like HTML

- `npm install -g create-react-app` creats a react application and Babel that compiles JSX and ES6+ into ES5 Javascript - this takes care of version discrepencies at various environment `-g` regers to global

- `create-react-app <app name>` will setup the default folders

- It also integrates 'handlebars' type functionality {} = {{}} of handlebars

- `npm start` to start the react app

- By default there is a `public` folder and a `src` folder. The public folder contains the `index.html` It is the single page of the react app that will display all the components of the react application. It contains the root <div> that will contain the app and the app intern contains all the components


- A `prop` is a function that is passed into a component from outside and can be used inside a component

- When ever JSX is used the react library should be imported

## Using React Bootstrap

- 