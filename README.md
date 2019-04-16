# CS52 Workshops:  CSS in JavaScript

![](http://i.giphy.com/eUh8NINbZf9Ys.gif)

Brief motivation here as well as in presentation

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

## Step 1: Add your API Key

Before we begin styling, edit the `youtube-api.js` file to include your API key.  You should use the same key you used for the short assignment. 

Now start up your webpack-dev-server!  Open the localhost in your browser, and you should see the SA4 frontend webapp with some basic styling.

```
yarn start
```

## Step 2: Let's get stylin'

Now that we’ve made sure the webapp is functioning, let’s put our new CSS in JS skills to the test.

* Explanations of the what **and** the why behind each step. Try to include:
  * higher level concepts
  * best practices

Remember to explain any notation you are using.

```javascript
/* and use code blocks for any code! */
```


## Step ??: Creating a Nav Bar
We're going to create a Navigation Bar from scratch and add some nice styled-components to it!
Create a new file in your /src folder called ```nav-bar.js```. We're going to start with the bare bones of a navigation bar and see how we'd style it. 

Here's a resource for [github markdown](https://guides.github.com/features/mastering-markdown/).


## Summary / What you Learned

* [ ] can be checkboxes

## Reflection

*2 questions for the workshop participants to answer (very short answer) when they submit the workshop. These should try to get at something core to the workshop, the what and the why.*

* [ ] 2 reflection questions
* [ ] 2 reflection questions


## Resources

* cite any resources
