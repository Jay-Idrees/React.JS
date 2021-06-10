# React by Facebook

This readme file is my personal collection of basic infromation and tips about react from various sourees including the materials from the Columibia University software engineering course Udemy and my own experience. I have created this repository as a quick reference for myself, so I have only included the deescriptions that I would want to refer back to in the future. 

## React Packages

- `ReactDOM` takes the tree of components and renders them on the DOM. `npm install react-dom`
- `Bootstrap` will install bootstrap. `npm install --save bootstrap` and then import `import 'bootstrap/dist/css/bootstrap.min.css';` to the `index.js` file


## General points about React and Installation
- Uses JSX code which javascrpt code that looks like HTML

- **Installation**

- `npm install create-react-app` creats a react application and Babel that compiles JSX and ES6+ into ES5 Javascript - this takes care of version discrepencies at various environments/browsers. 

- `npx create-react-app <app name>` will setup the default folders, Npx is a package itself that comes with npm and will execute pakages. Here it is being used to execute the create-react-app package. This will automatically create `.gitignore` file to prevent node modules from being pushed to the repository

- Here `npm uninstall --global create-react-app` to uninstall a global package

- It also integrates 'handlebars' type functionality {} = {{}} of handlebars

- `npm start` to start the react app

- By default there is a `public` folder and a `src` folder. The public folder contains the `index.html` It is the single page of the react app that will display all the components of the react application. It contains the root < div > that will contain the app and the app intern contains all the components as props. The the props are then passed on as parameter into the function of that component. Below is a good example



## Props

- A `prop` is a function that is passed into a component from outside and can be used inside a component

- Whenever JSX is used the react library should be imported with `import React from "react";`

- In `app.js` the function App is also a component, all 'children' components must be contained inside a <div>

- When using `props` the data first comes into the App.js - the final app component - it can be either from a form or is imported from a JSON file or some database (SQL, Mongo DB). Each of the fields of the data are then tagged and using the tags passed onto the individual components


- Inside `app.js` located inside the src folder

```javascript
import React from "react";
import Wrapper from "./components/Wrapper";
import Title from "./components/Title";
import FriendCard from "./components/FriendCard";
import friends from "./friends.json"; 
// Note that the data is imported here from JSON file called friends.json.
// This file contains an array of objects. Each object consist of name, image, occupation and location
// Here you are giving a generic name to each object group "friends"

function App() {
  return (
    <Wrapper>
      <Title>Friends List</Title>
      <FriendCard
      // Here you are selecting the first object [ordered as 0] from the array and 
      // then specifically extracting name or image etc
        name={friends[0].name}
        image={friends[0].image}
        occupation={friends[0].occupation}
        location={friends[0].location}
      />   
      <FriendCard
// Here you load the component into the app
// Then you pass on the data elements as props
// Then the component gets loaded with the data that is specified
// The final component with data is then generated in the app component
// data (form or some database)-> App.js -> Component as props -> updated component with data -> Final 
// component is then generated in app.js
        name={friends[1].name}
        image={friends[1].image}
        occupation={friends[1].occupation}
        location={friends[1].location}
      />
      <FriendCard
        name={friends[2].name}
        image={friends[2].image}
        occupation={friends[2].occupation}
        location={friends[2].location}
      />
    </Wrapper>
  );
}

export default App;
```

- Inside the FriendCard component. This is located in the component folder, which is located in the src folder of the react app

```javascript
import React from "react";
import "./style.css";

// Note that here adding props is giving the component the capability to receive data
// What data is received is determined by what data is imported into the App component
function FriendCard(props) {
  return (
    <div className="card">
      <div className="img-container">
        <img alt={props.name} src={props.image} />
      </div>
      <div className="content">
        <ul>
          <li>
            <strong>Name:</strong> {props.name}
          </li>
          <li>
            <strong>Occupation:</strong> {props.occupation}
          </li>
          <li>
            <strong>Location:</strong> {props.location}
          </li>
        </ul>
      </div>
    </div>
  );
}

export default FriendCard;
```


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

## Using Bootstrap in React

- `import 'bootstrap/dist/css/bootstrap.min.css';` should be added to the `index.js` file in the react app if bootstrap is to be used- similar to linking in the HTML header page


## CSS Styling of React Components

- There are two ways
    - 1) Local styling inside the component, like we use the <style><style> method in html for styling a local page and then invoking them inside the <div>
    - 2) Creating a new styles folder and then creating new css files inside the folder specific to components such as navbar or jumbotron. Then the css classes can be invoked inside the components as "className=xyz" inside the component <div> See examples below
    - You can also use both these methods together. For instance you can use style before class name to change any background in the standard section class

```javascript

// Local styling inside the component

import React from "react";

// Note that here the styles is an object. 
// Unlike HTML where you can invoke style as string, in react it must be an object

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
      // Note the difference, styles.card is object oriented programming
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
- Importing CSS classes inside the react components from css files in the styles folder

```javascript

import React from "react";
import "../styles/Header.css";

function Header() {
  return (
    <header className="header">
      <h1>Home</h1>
    </header>
  );
}

export default Header;
```

- The corresponding CSS file in style folder
```css
.header {
  background: #f9b713;
  height: 200px;
}

.header h1 {
  margin: 0;
  padding-top: 75px;
  text-align: center;
  color: white;
  font-size: 3rem;
}
```

- Using both Style and ClassName together

```javascript
import React from "react";
// Note the section file imported form the styles folder to be invoked inside the component
import "../styles/Section.css";


const styles = {
  sectionStyles: {
    background: "orange"
  }
};

// The section component code
function Section() {
  return (
    <section style={styles.sectionStyles} className="section">
      <h2>Example Heading</h2>
      <p>
        Example text
      </p>
      
    </section>
  );
}

export default Section;
```

- Some basic code for index.css
```css
* {
  box-sizing: border-box;
  font-family: sans-serif;
}

html, body, #root {
  padding: 0;
  margin: 0;
  height: 100%;
}
```

## Using MAP and FILTER for listing in React

- In addition to database or form, the source of the data can also be a variable. In this example you can see a list of groceries is used that is stored in a groceries variable

- In the app.js in the src folder:

```javascript

import React from "react";
import List from "./components/List";

// This is an object called groceries containing individual items composed of data elements
const groceries = [
    // It is an array of objects
  {
    id: 1,
    name: "Milk",
    purchased: true
  },
  {
    id: 2,
    name: "Eggs",
    purchased: true
  },
  {
    id: 3,
    name: "Cheese",
    purchased: false
  },
  {
    id: 4,
    name: "Cake Mix",
    purchased: false
  },
  {
    id: 5,
    name: "Carrots",
    purchased: false
  },
  {
    id: 6,
    name: "Juice",
    purchased: true
  }
];

function App() {
  return <List groceries={groceries} />;
}

export default App;
```

- Then in the list component file which is in the components folder in the src folder

```javascript
function List(props) {
  return (
//Here the class name is the standard class as used with bootstrap. 
// Same like before, app.js loads groceries data from the groceries object
// Passes it on to the list component
// The updated final component with loaded data is then generated in app.js
// Here you are also modifying the data loaded using map, so the text list gets appropriate styling
// The purpose of key is for react to track changes for a particular element
    <ul className="list-group">
      {props.groceries.map(item => (
        <li className="list-group-item" key={item.id}>
          {item.name}
        </li>
      ))}
    </ul>
  );
}

export default List;
```
- OR

```javascript
import React from "react";

function List(props) {
  // A new variable is created that only contains the groceries that are not purchased
  // Note that the groceries object contains true/false element for each sub-object with purchased element
  // !item.purchased is shortlisting only the items that have purchased element specified as false
  const notPurchased = props.groceries.filter(item => !item.purchased);

  return (
    <ul className="list-group">
      {notPurchased.map(item => (
        <li className="list-group-item" key={item.id}>
          {item.name}
        </li>
      ))}
    </ul>
  );
}

export default List;
```
