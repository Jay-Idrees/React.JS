# React by Facebook

This readme file is my personal collection of basic infromation and tips about react from various sourees including the materials from the Columibia University software engineering course Udemy and my own experience. I have created this repository as a quick reference for myself, so I have only included the deescriptions that I would want to refer back to in the future. 

## React Packages

- `ReactDOM` takes the tree of components and renders them on the DOM. `npm install react-dom`
- `Bootstrap` will install bootstrap. `npm install --save bootstrap` and then import `import 'bootstrap/dist/css/bootstrap.min.css';` to the `index.js` file


## General points about React nad Installation
- Uses JSX code which javascrpt code that looks like HTML

- **Installation**

- `npm install create-react-app` creats a react application and Babel that compiles JSX and ES6+ into ES5 Javascript - this takes care of version discrepencies at various environments/browsers. 

- `npx create-react-app <app name>` will setup the default folders, Npx is a package itself that comes with npm and will execute pakages. Here it is being used to execute the create-react-app package. This will automatically create `.gitignore` file to prevent node modules from being pushed to the repository

- Here `npm uninstall --global create-react-app` to uninstall a global package

- It also integrates 'handlebars' type functionality {} = {{}} of handlebars

- `npm start` to start the react app

- By default there is a `public` folder and a `src` folder. The public folder contains the `index.html` It is the single page of the react app that will display all the components of the react application. It contains the root <div> that will contain the app and the app intern contains all the components


**React Specifics**

- A `prop` is a function that is passed into a component from outside and can be used inside a component

- When ever JSX is used the react library should be imported with `import React from "react";`

- In `app.js` the function App is also a component, all 'children' components must be contained inside a <div>

- React used `className` instead of class, because `class` is a keyword in javascript and as JSX is an extension of the javascript so using class in JSX would be like using a javascript command which can create unintended problems

```javascript
function App() {
  return (
    <div className="container">
      <Navbar />
      <Jumbotron />
      <Card />
    </div>
  );
}

export default App;
```

`ReactDOM.render(<App />, document.getElementById('root'));` whould be included in the `index.js` for react to render these components into the root directory of `index.html`

- We can use variables and functions inside the component by placing it in the javascript curly brackets {}. We can also use math.random in this way

```javascript
function component() {
  return (
    <div className="main-container">
      <div className="container">
        <div className="jumbotron">
          <h1>Hi! My name is ({name})</h1>
          <h2>My name has ({name.length}) letters</h2>
          <h2>My name without any vowels is: ({stripVowels(name)})</h2>
          <h2>I think React ({thoughts})</h2>
        </div>
      </div>
    </div>
  );
}
```

## Using React Bootstrap

- `import 'bootstrap/dist/css/bootstrap.min.css';` should be added to the `index.js` file in the react app if bootstrap is to be used- similar to linking in the HTML header page


## Handeling styling with react

- There are two ways
    - 1) Local styling inside the component, like we use the <style><style> method in html for styling a local page and then invoking them inside the <div>
    - 2) Creating a new styles folder and then creating new css files inside the folder specific to components such as navbar or jumbotron. Then the css classes can be invoked inside the components as "className=xyz" inside the component <div> See examples below

```javascript

- Local styling inside the component

import React from "react";

const styles = {
  card: {
    margin: 20,
    background: "#e8eaf6"
  },
  heading: {
    background: "#3f51b5",
    minHeight: 50,
    lineHeight: 3.5,
    fontSize: "1.2rem",
    color: "white",
    padding: "0 20px"
  },
  content: {
    padding: 20
  }
};

function Card() {
  return (
    <div style={styles.card}>
      <div style={styles.heading}>Lorem ipsum dolor</div>
      <div style={styles.content}>
        "example text"
      </div>
    </div>
  );
}

export default Card;

```