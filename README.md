# CS52 Workshops:  CSS in JavaScript

![](https://media.giphy.com/media/fs68M1NGzYwv0aQmhO/giphy.gif)

Why does this matter?  Well, as we learned today, not all CSS features work with JavaScript event handlers. Darn! Soooo JS? 
YES! With JS, CSS is generated, you can use every media query and pseudo selector. Some libraries (like jss, styled-components) even add support for cooool, non-CSS-native features.
Gone are the days of long style sheets. Here to stay is CSS in JS.

As we learned in class, some highlights of style-components 

**Automatic critical CSS:** styled-components keeps track of which components are rendered on a page and injects their styles and nothing else, fully automatically. **Easier deletion of CSS:** If the component is unused (which tooling can detect) and gets deleted, all its styles get deleted with it. **Simple dynamic styling:** adapting the styling of a component based on its props or a global theme is simple and intuitive without having to manually manage dozens of classes. **Painless maintenance:** you never have to hunt across different files to find the styling affecting your component, so maintenance is a piece of cake no matter how big your codebase is. **Automatic vendor prefixing:** write your CSS to the current standard and let styled-components handle the rest.

(source: hackernoon.com)

## Overview

At this point, we have all (hopefully) finished Short Assignment 4 and have some experience using React to build a video application.  For this workshop, we are going to restyle our SA4 using CSS in JS.  We’ll walk you through this process step by step, but feel free to change the styles up as you go!

## Setup

Download/clone your own copy of this repo so you have all of the necessary code on your computer. Cd into the workshop-css-in-js-workshop folder (if you couldn’t tell, this is a workshop). You should have a README.md, img folder, package.json, src folder, webpack.config.js, and yarn.lock. Since we are using javascript styling instead of CSS now, most of the files we will be working with will be javascript files. 

Let's take care of a few more set-up steps before we begin (check again to make sure you are in the correct directory!).
As we did in SA4, start by adding in support for React and JSX in babel: 

```
yarn add --dev @babel/preset-react @babel/plugin-proposal-class-properties
```

Now let’s take care of all our dependencies: 

```
yarn add lodash.debounce react react-dom react-router axios
```

## Step by Step

### Step 1: Add your API Key

Before we begin styling, edit the `youtube-api.js` file to include your API key.  You should use the same key you used for the short assignment. 

Now start up your webpack-dev-server!  Open the localhost in your browser, and you should see the SA4 frontend webapp with some basic styling.

```
yarn start
```

### Step 2: Let's get stylin'

Now that we’ve made sure the webapp is functioning, let’s put our new CSS in JS skills to the test.

* Explanations of the what **and** the why behind each step. Try to include:
  * higher level concepts
  * best practices

Remember to explain any notation you are using.

```javascript
/* and use code blocks for any code! */
```


### Step ??: Creating a Nav Bar
We're going to create a Navigation Bar from scratch and add some nice styled-components to it!
Create a new file in your /src folder called ```nav-bar.js```. We're going to start with the bare bones of a navigation bar and see how we'd style it. 
```
/* eslint-disable jsx-a11y/anchor-is-valid */
/* eslint-disable react/prefer-stateless-function */

import React, { Component } from 'react';

class Navbar extends Component {
  render() {
    return (
      <Bar>
        <Button>MyTube</Button>
        <List>
          <ListItem><a href="#">Home</a></ListItem>
          <ListItem><a href="#">About</a></ListItem>
          <ListItem><a href="#">FAQ</a></ListItem>
          <ListItem><a href="#">Contact</a></ListItem>
        </List>
      </Bar>
    );
  }
}

export default Navbar;
```
... Wait a second, what's ```<Bar>```? What's ```<Button>```? What's ```<List>``` and ```<ListItem>```? Great question! For styled-components, we will define a ```const Bar, Button, List,``` and ```ListItem``` that will be a styled div, button, ul, and li. styled-components lets us essentially create classes for each element by declaring them as ```const```.  Go ahead and add the following code above your class Navbar:

```
const Bar = styled.div`
display: flex;
flex-direction: row;
justify-content: space-between;
border: 2px solid #F05252;
box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.15);
margin: 2em 0;
padding: 2em 2em;
border-radius: 3px;
`;
const Button = styled.button`
color: white;
padding: 0 2em;
margin: 0 1em;
background: #F05252;
border: 2px solid #F05252;
border-radius: 3px;
`;
const List = styled.ul`
display: flex;
flex-direction: row;
justfy-content: space-around;
list-style-type: none;
margin: 0em 2em;
`;
const ListItem = styled.li`
padding: 0 2em;
color: #F05252;
`;
```

Now let's import Navbar to your ```index.js``` file:

```
import Navbar from './components/nav_bar';
```

and add it above your ```<SearchBar/>``` in the render function:
```
<div><Navbar /></div>
```

Your navbar should look something like this:
<img width="1015" alt="Screen Shot 2019-04-16 at 11 31 40 AM" src="https://user-images.githubusercontent.com/38498065/56223603-13eb4200-603c-11e9-8b40-5ba93dcf0e80.png">

Quite often you might want to use a component, but change it slightly for a single case. For example, you might want to use our button for the navigation menu links, but you want them to look slightly different. You could pass in a function and then change them based on some props, but that's a lot of code and effort for a small change. 

What we're going to do is make a new component that inherits the styling of another. We'll wrap it in the styled() constructor and extend/replace some styling. 

To change the ListItem links, we're going to make a new component ListItem2:
```
const ListItem2 = styled(Button)`
color: #F05252;
background: white;
`;
```
Now replace our previous list of ListItem with the following code:
```
<ListItem2 as="a" href="/">Home</ListItem2>
<ListItem2 as="a" href="/">About</ListItem2>
<ListItem2 as="a" href="/">FAQ</ListItem2>
<ListItem2 as="a" href="/">Contact</ListItem2>
```

What we've done here is use the "as" polymorphic prop to dynamically swap out the element that receives the styles for Button. Here, the element ```a``` pretends it's a button but ultimately gets rendered out as a hyperlink. Pretty cool, and very useful for more robust navigation bars you might make in the future. 

Here's what you should end up with:
<img width="1038" alt="Screen Shot 2019-04-16 at 11 32 10 AM" src="https://user-images.githubusercontent.com/38498065/56223601-13eb4200-603c-11e9-8adc-cd2af31bbb37.png">

Here's a resource for [github markdown](https://guides.github.com/features/mastering-markdown/).


## Summary / What you Learned

**What your site has:**
* [ ] A redesigned Short Assignment 4, but this time with styled-components
* [ ] A Navigation Bar that serves as the basis for future navigation bars

**What you learned:**
* [ ] The various ways in which you can incorporate CSS in JS
* [ ] The advantages and limitations of styled-components
* [ ] The basics of using styled-components
* [ ] Ways of extending styled-components to adapt one style to another

## Reflection

*2 questions for the workshop participants to answer (very short answer) when they submit the workshop. These should try to get at something core to the workshop, the what and the why.*

* [ ] 2 reflection questions
* [ ] 2 reflection questions


## Resources

* cite any resources
