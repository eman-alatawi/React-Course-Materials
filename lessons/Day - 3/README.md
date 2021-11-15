## Event Handling

###  Events in React:
 An event gets triggered when a user performs some action causing the change of state. Handling events in React is similar to handling HTML DOM element events.
 - React events use `camelCase` syntax for naming. Ex: `onClick()`
 - Event handlers are written inside curly braces. Ex: `onClick={print}`
- With JSX you pass a function as the event handler.
 - To prevent the default behavior, explicitly call the `preventDefault()` method.
   ```js
    function handleClick(e) {
        e.preventDefault();
    }
    ```
![Event handlers](./images/Event-handlers.png)

### Bind `this`:
- In JavaScript, class methods are not bound by default.
 - Needed only in case of `Class components`.
 - `this` represents the component that owns the method.
 -  Use `arrow functions () => {}` to avoid confusion about `this`.

![class functions](./images/class-function.jpg)

### Notes:

![class functions](./images/Notes.png)

- [Event Handlers example in codesandbox](https://codesandbox.io/s/sandpack-project-forked-muos6)

### Event propagation:
Event handlers will also catch events from any children your component might have. We say that an event “bubbles” or “propagates” up the tree: it starts with where the event happened, and then goes up the tree.


### Stopping propagation:

Event handlers receive an event object as their only argument. By convention, it’s usually called e, which stands for “event.” You can use this object to read information about the event.

That event object also lets you stop the propagation. If you want to prevent an event from reaching parent components, you need to call `e.stopPropagation()`

- [Event Propagation example in codesandbox](https://codesandbox.io/s/sandpack-project-forked-t7zmy)


## Practice Time (Simple Gallery App)

![gallery-app](./images/gallery-1.png)
![gallery-app](./images/gallery-2.png)
![gallery-app](./images/gallery-3.png)

- Your app sturcture should look like this:

```
/gallery-app
   /src
    /App.js
    /index.js
    /data.js
    /components
      /Gallery.js 
```
- use this Sculpture list below in your app
- `data.js`

```js
export const sculptureList = [{
    name: 'Homenaje a la Neurocirugía',
    artist: 'Marta Colvin Andrade',
    description: 'Although Colvin is predominantly known for abstract themes that allude to pre-Hispanic symbols, this gigantic sculpture, an homage to neurosurgery, is one of her most recognizable public art pieces.',
    url: 'https://i.imgur.com/Mx7dA2Y.jpg',
    alt: 'A bronze statue of two crossed hands delicately holding a human brain in their fingertips.'
  }, {
    name: 'Floralis Genérica',
    artist: 'Eduardo Catalano',
    description: 'This enormous (75 ft. or 23m) silver flower is located in Buenos Aires. It is designed to move, closing its petals in the evening or when strong winds blow and opening them in the morning.',
    url: 'https://i.imgur.com/ZF6s192m.jpg',
    alt: 'A gigantic metallic flower sculpture with reflective mirror-like petals and strong stamens.'
  }, {
    name: 'Eternal Presence',
    artist: 'John Woodrow Wilson',
    description: 'Wilson was known for his preoccupation with equality, social justice, as well as the essential and spiritual qualities of humankind. This massive (7ft. or 2,13m) bronze represents what he described as "a symbolic Black presence infused with a sense of universal humanity."',
    url: 'https://i.imgur.com/aTtVpES.jpg',
    alt: 'The sculpture depicting a human head seems ever-present and solemn. It radiates calm and serenity.'
  }, {
    name: 'Moai',
    artist: 'Unknown Artist',
    description: 'Located on the Easter Island, there are 1,000 moai, or extant monumental statues, created by the early Rapa Nui people, which some believe represented deified ancestors.',
    url: 'https://i.imgur.com/RCwLEoQm.jpg',
    alt: 'Three monumental stone busts with the heads that are disproportionately large with somber faces.'
  }, {
    name: 'Blue Nana',
    artist: 'Niki de Saint Phalle',
    description: 'The Nanas are triumphant creatures, symbols of femininity and maternity. Initially, Saint Phalle used fabric and found objects for the Nanas, and later on introduced polyester to achieve a more vibrant effect.',
    url: 'https://i.imgur.com/Sd1AgUOm.jpg',
    alt: 'A large mosaic sculpture of a whimsical dancing female figure in a colorful costume emanating joy.'
  }, {
    name: 'Ultimate Form',
    artist: 'Barbara Hepworth',
    description: 'This abstract bronze sculpture is a part of The Family of Man series located at Yorkshire Sculpture Park. Hepworth chose not to create literal representations of the world but developed abstract forms inspired by people and landscapes.',
    url: 'https://i.imgur.com/2heNQDcm.jpg',
    alt: 'A tall sculpture made of three elements stacked on each other reminding of a human figure.'
  }, {
    name: 'Cavaliere',
    artist: 'Lamidi Olonade Fakeye',
    description: "Descended from four generations of woodcarvers, Fakeye's work blended traditional and contemporary Yoruba themes.",
    url: 'https://i.imgur.com/wIdGuZwm.png',
    alt: 'An intricate wood sculpture of a warrior with a focused face on a horse adorned with patterns.'
  }, {
    name: 'Big Bellies',
    artist: 'Alina Szapocznikow',
    description: "Szapocznikow is known for her sculptures of the fragmented body as a metaphor for the fragility and impermanence of youth and beauty. This sculpture depicts two very realistic large bellies stacked on top of each other, each around five feet (1,5m) tall.",
    url: 'https://i.imgur.com/AlHTAdDm.jpg',
    alt: 'The sculpture reminds a cascade of folds, quite different from bellies in classical sculptures.'
  }, {
    name: 'Terracotta Army',
    artist: 'Unknown Artist',
    description: 'The Terracotta Army is a collection of terracotta sculptures depicting the armies of Qin Shi Huang, the first Emperor of China. The army consited of more than 8,000 soldiers, 130 chariots with 520 horses, and 150 cavalry horses.',
    url: 'https://i.imgur.com/HMFmH6m.jpg',
    alt: '12 terracotta sculptures of solemn warriors, each with a unique facial expression and armor.'
  }, {
    name: 'Lunar Landscape',
    artist: 'Louise Nevelson',
    description: 'Nevelson was known for scavenging objects from New York City debris, which she would later assemble into monumental constructions. In this one, she used disparate parts like a bedpost, juggling pin, and seat fragment, nailing and gluing them into boxes that reflect the influence of Cubism’s geometric abstraction of space and form.',
    url: 'https://i.imgur.com/rN7hY6om.jpg',
    alt: 'A black matte sculpture where the individual elements are initially indistinguishable.'
  }, {
    name: 'Aureole',
    artist: 'Ranjani Shettar',
    description: 'Shettar merges the traditional and the modern, the natural and the industrial. Her art focuses on the relationship between man and nature. Her work was described as compelling both abstractly and figuratively, gravity defying, and a "fine synthesis of unlikely materials."',
    url: 'https://i.imgur.com/okTpbHhm.jpg',
    alt: 'A pale wire-like sculpture mounted on concrete wall and descending on the floor. It appears light.'
  }, {
    name: 'Hippos',
    artist: 'Taipei Zoo',
    description: 'The Taipei Zoo commissioned a Hippo Square featuring submerged hippos at play.',
    url: 'https://i.imgur.com/6o5Vuyu.jpg',
    alt: 'A group of bronze hippo sculptures emerging from the sett sidewalk as if they were swimming.'
  }];
  
```

- `App.js`

```js
import Gallery from './components/Gallery';
import './App.css';
function App() {
  return (
    <div className="app-container">
      <h2>Sculpture List</h2>
      <Gallery/>
    </div>
  );
}

export default App;
```

- `Gallery.js`
```js
import React, { Component } from "react";
import { sculptureList } from "../data";

export default class Gallery extends Component {
  constructor() {
    super();
    this.state = {
      index: 0,
      showMore: false,
    };
  }

  handleNextClick = () => {
    if (this.state.index + 1 < sculptureList.length) {
      this.setState({
        index: this.state.index + 1,
      });
    } else {
      this.setState({
        index: 0,
      });
    }
  };

  handleMoreClick = () => {
    this.setState({
      showMore: !this.state.showMore,
    });
  };

  render() {
    const { index, showMore } = this.state;
    let sculpture = sculptureList[index];

    return (
      <div className="container">
        <section>
          <div className="top-container">
            <button onClick={this.handleNextClick}>Next &gt;&gt; </button>

            <h4>
              <i>{sculpture.name} </i>
              by {sculpture.artist}
            </h4>
            <h5>
              ({index + 1} of {sculptureList.length})
            </h5>
          </div>
          <button onClick={this.handleMoreClick}>
            {showMore ? "Hide" : "Show"} details
          </button>
          {showMore && <p>{sculpture.description}</p>}
        </section>

        <img src={sculpture.url} alt={sculpture.alt} />
      </div>
    );
  }
}

```

- `App.css`
```css
* {
  box-sizing: border-box;
}

body {
  font-family: sans-serif;
  padding: 0;
  margin: 0;
}

.app-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: rgb(33, 16, 94);
  height: 100vh;
}
h2 {
  color: whitesmoke;
}

h4,
h5 {
  text-align: center;
}

h5 {
  color: rgb(247, 163, 9);
}

.container {
  background-color: whitesmoke;
  padding: 1rem;
  display: flex;
  flex-direction: row-reverse;
  justify-content: space-between;
  align-items: center;
  color: #343434;
  border-radius: 0.5rem;
}

section {
  padding: 0 1rem;
  width: 60rem;
  height: 20rem;
  text-align: center;
}

.top-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

button {
  margin: 1rem !important;
  padding: 0.5rem 1.5rem;
  border: none;
  background-color: rgb(247, 163, 9);

  border-radius: 2rem !important;
  color: aliceblue;
  font-size: medium;
}

button:hover {
  background-color: rgb(67, 43, 152);
}

img {
  width: 20rem;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}

p {
  padding: 0 12rem;
  text-align: center;
  margin-top: 2rem;
  color: rgb(47, 41, 69);
}
```


