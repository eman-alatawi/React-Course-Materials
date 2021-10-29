## What Is React?

 React is a declarative, efficient, and flexible JavaScript library for building user interfaces. It lets you compose complex UIs from small and isolated pieces of code called Components.

 - A client side JavaScript library, created and maintained by Facebook.

 - Referred to as V in the Model-View- Controller (MVC) architecture.
 
### React is Declarative?
- React makes it painless to create interactive UIs.
- Design simple views for each state in your application, and React will efficiently update and render just the right components when your data changes.

###  Why Should We Select React?
- Easy to learn and use
- Reusable components
- Highly stable, scalable, and efficient
- Virtual Document Object Model
- Faster and flexible development
- Easier debugging and testing

#### Common examples of React web apps:
- Facebook
- Instagram
- Twitter
- Netflix
- Airbnb
- Uber

###  Single-Page Application:
A single-page application works inside a browser and requires no page reloads and extra wait time. It uses AJAX and HTML5 to build responsive apps like React.

## Installing React
### Prerequisites:
- Node.js and NPM
  - Node.js is a Javascript run-time environment that allow us to execute Javascript code like if we were working on a server.
  - NPM is Node Package Manager for Javascript. Allows us to easily install Javascript libraries.
  - check the node and npm versions in your local system:
    - ``` node -v ```
    - ``` npm -v ```

### Install ReactJS using create-react-app

```
npx create-react-app your-app-name
```


##  React Basics

###  What Is JSX?
 JSX (JavaScriptXML) is a syntax extension of JavaScript and is used to produce React elements. It describes how the UI should look and permits the addition of HTML in JavaScript code.

 - Makes code short and concise and easy to understand

### JSX Expressions
 - Any JavaScript expression embedded inside curly braces `{}` is acceptable to JSX.
 - It can be used inside any conditional statement or loop in JS.
 - Declare a variable using const to use it inside JSX within curly braces.

 ```javascript
 const name = 'ABC';
const element = <h1>Hello, {name}</h1>;

 ```

###  JSX Restrictions

- class is a reserved word in JavaScript and is used in React components such as `class App extends Component {}`. It cannot be used inside JSX expressions. Instead, `className` can be compiled as a class.

- A JSX expression requires one root element or a `<div>` to wrap all elements for styling them, though the root element can be empty for Fragments.

``` javascript
<>
    <h1>This is Heading</h1>
    <p>This is Paragraph</p>
</>
```

- `()` is used after the `return` keyword to render the JSX on the page. It allows to return correctly structured HTML across multiple lines without any errors.

- Cannot use `if-else` inside JSX But you can use ternary! `?:`


### React with/without JSX :

``` javascript
// With JSX
const myelement = <h1>First JSX element!</h1>;
ReactDOM.render(myelement, document.getElementById('root'));

```

``` javascript
// Without JSX
const myelement = React.createElement('h1', {}, 'no JSX!');
ReactDOM.render(myelement, document.getElementById('root'));
```

## React Components


### 1- Stateful component / class component
- A stateful component is a class component, created by extending the React Component class. It depends on its state object and can change its own state.

- This is considered as the `old way` of defining components in React
- The component rerenders based on changes made to its state. It can pass its state properties to its child components.

- It has Component Lifecycle methods like:
     - `Constructor()`: is the very first method to be called on instantiating any React component. It helps in initializing the state of a component.
    - `componentDidMount()`: Called only once but just after the render() method. 
    - `componentDidUpdate()`: is called after the changes are updated in the DOM.
    - `componentWillUnmount()`: last function that is called just before removing components from the DOM.

- You can access props via this.props
- You can access state using this.state

``` javascript
class Main extends Component { 
    constructor() {
        super()
        this.state = {
         books: [] 
        }
    } 

    render() {
        return (
        <BooksList books={this.state.books} />
        )
    }
}
    
```

### Component Render:
- Every component must have render function
- It should return single React object `<></>`
- Changing state in render function is not allowed, do not call `setState` inside it.
- Component renders when props or state changes.

### 2- Stateless component / Functional Component
- A stateless component is often considered a concept presented to the user, thus also known as Presentation components.
- It is very much like a function that accepts props as an input and returns a React element. 
- Stateless components that lack lifecycle
methods. React hook like `useEffect` should give you most of what you'd need.

- use `React hooks` to add states using `useState()`.
- 

``` javascript
const BooksList = ({books}) => {
 return (
     <ul>
        {books.map(book => (
         <li>book</li>
         ))
        }
     </ul> 
    )
}

```


## States And Props

### 1- States
- It represents data internal to the component.
- It is objects which supplies data to component.
- Controlled by the component.
- It is an object that holds information which might change over the component lifecycle.
- Record and respond to user events.
- Changes over time based on user input.
- Modified using `this.setState()`
- States can be initilized by props.

``` javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      array: [3,4],
      userName: 'Sara'
    };
}
  changeUserName = () => {
    // NOTE: this will NOT change this.state.array
    this.setState({
      userName: 'Nora'
    });
}
  render() {
    return (
     <div> 
        <p>
          It is a {this.state.userName}
        </p>
        <button
          type="button"
          onClick={this.changeUserName}
          >Change UserName
        </button>
      </div>
    );
 }
}

```

### 2- Props

- Props are used to communicate between components.
- Props are immutable, readonly
You will get an error if you try to change their value.
- Always passed down from parent to child.

``` javascript
// In Parent component
<Child name="Dan" id="101"></Child>
// Child component definition
<h1>{props.name}</h1>
<p>{props.id}</p>

```

## Practice Time (Simple Movies App)

- Create react app that renders list of movies using class component and functional component as required.

![movies-app](./images/movies-app.png)


- Your app sturcture should look like this:

```
/movies-app
   /src
    /App.js
    /index.js
    /MoviesData.js
    /components
      /styles
        /Container.styled.js
        /Movie.styled.js
        /Movies.styled.js
      /Movies.js
      /Movie.js  
```
- use this movies list in your app:
``` javascript
{
        movie_id: 1,
        title: "The Girl Riding a Bulldozer",
        description:
          "“The Girl Riding a Bulldozer” will tell the story of Hye Young, who investigates her father’s whereabouts after he suffers an unexpected accident. Yesung will take on the role of detective Go Yoo Suk, who is in charge of the case involving Hye Young’s father.",
        release_Date: 2021,
        poster_src: "https://i.mydramalist.com/1lnER_4f.jpg",
      },
      {
        movie_id: 2,
        title: "My Korean Teacher",
        description:
          "After being dumped by his girlfriend, the company Yong Woon works for goes bankrupt while he is in Okinawa on a business trip, so he needs employement. Single mother Sakura works for a travel agency and needs to learn Korean for her job. She then meets Yong Woon at a Korean language institute and their romance begins.",
        release_Date: 2016,
        poster_src: "https://i.mydramalist.com/yNxjNf.jpg",
      },
      {
        movie_id: 3,
        title: "I AM.",
        description:
          "Behind the 5 minutes of fame and dazzle on stage are years of unseen practice and effort. SMTOWN is one of South Korea’s largest record labels and home to some of K-pop's top artists, including BoA, TVXQ, GIRL’S GENERATION, SUPER JUNIOR, and more. “I AM” follows the past and present lives of these SMTOWN artists through never-before-seen audition tapes, practice clips, and private interviews. Embellished with performances from SMTOWN’s historic concert at New York’s Madison Square Garden, the film presents an intriguing and poignant look into the lives of the young stars.",
        release_Date: 2012,
        poster_src: "https://i.mydramalist.com/wOplpf.jpg",
      },
    ];
```

- use styled component for styling using the command below:

```
npm install --save styled-components
```

- `App.js`

``` javascript
import Movies from "./components/Movies";
import { Container } from "./components/styles/Container.styled";
import React, { Component } from "react";

export default class App extends Component {
  constructor() {
    super();
    this.state = {
      welcome: "Welcome to the movies app",
    };
  }

  render() {
    return (
      <Container>
        <h1>{this.state.welcome}</h1>
        <Movies />
      </Container>
    );
  }
}
```

- `Movies.js`

``` javascript
import React, { Component } from "react";
import { StyledMovies } from "./styles/Movies.styled";
import Movie from "./Movie";
import moviesData from "../MoviesData";

export default class Movies extends Component {
  constructor() {
    super();
    this.state = {
      movies: moviesData,
    };
  }
  render() {
    const { movies } = this.state;
    const moviesList = movies.map((movie) => (
      <Movie key={movie.movie_id} {...movie} />
    ));
    return (
      <StyledMovies>
        {moviesList}
      </StyledMovies>
    );
  }
}
```

- `Movie.js`

``` javascript
import React from 'react'
import {StyledMovie} from './styles/Movie.styled'

function Movie({title, description, release_Date, poster_src}) {
    return (
        <StyledMovie>
            <h4>{title} | {release_Date}</h4>
            <div className="img-container">
            <img src={poster_src}/>
            </div>
           
            <p>{description}</p>
        </StyledMovie>
    )
}

export default Movie
```


- `Container.styled.js`
``` javascript
import styled from "styled-components";

export const Container = styled.div`
  padding: 2rem;
  background-color: #f6f7f9;

  h1 {
    color: #404756;
    text-align: center;
  }
`;
```


- `Movies.styled.js`
``` javascript
import styled from "styled-components";

export const StyledMovies = styled.div`
  /* background-color: antiquewhite; */
  padding: 2rem;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 2em;
  align-items: center;
`;

```

- `Movie.styled.js`
``` javascript

import styled from "styled-components";

export const StyledMovie = styled.div`
  background-color: white;
  width: 20rem;
  height: 35rem;
  padding: 1rem;
  border-radius: 2rem;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;

  h4 {
    text-align: center;
  }

  .img-container {
    height: 15rem;
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
  }

  img {
    height: 100%;
    object-fit: cover;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;

    border-radius: 1rem;
  }
  p {
    height: 12rem;
    overflow-y: scroll;
    padding: 1rem;
    text-align: justify;
    line-height: 2.2rem;
  }
`;
```

Additional Resources:

  - [Styled Components ](https://styled-components.com/)


