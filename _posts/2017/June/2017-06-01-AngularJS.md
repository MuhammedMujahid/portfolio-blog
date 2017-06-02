---
layout: post
title:  "Angular 2"
date:   2017-06-01
excerpt: "Lets get an angle on this framework"
tag:
- AngularJS
- javscript

comments: false
---
## What the heck is Angular 2??
Well Google says Angular 2 is a modern JavaScript framework from Google commonly used to work with (SPAs).

## Great! So whats a SPA??
SPA stands for "Single Page Applications" and is a shell page in which we can load multiple views! Traditional application reloads everything at once, which is a waste of bandwidth. With a SPA and it's multiple views, you can load tid bits of the page seperately on the fly and embedded in the shell page. An example of a SPA would be gmail.

## Features of AngularJS
- It is a full featured framework and supports stuff like two way data binding, MVC...
- ... Built in routing support to load views..
- ... Jqlite is built in for dom manipulation...
- ... Data binding, we have full support for templates, share code through services...
- There's too much to list all here (i'm not paid enuff for this, actually i'm not paid at all. Please hire me)

## Typescript
- Typescript is a super set of javascript. Which means any javascript code will work as Typescript
- It brings some useful features that are missing in javascript supported by most browsers
- With typescript, we get modules, classes, interfaces, access modifiers, intellicence and compile time checking

## Building blocks of an Angular 2 Application
- Components, directives, routers and services.
### Components
- The component encapsulates template, data and the behaviour of a view
- So it would make sense to call it a view component
- Every angular 2 application has atleast 1 component, which we call the root component
- But most applications consist of many Components
- Lets take for example a page with a Navbar and sidebar, each of these components has html markup (template) as a view, as well as data and logic
- a component can have a component inside it. This helps break down components into manageable pieces
- Components are completely decoupled from the DOM, so instead we use binding in the view to bind the properties and methods of the component
- if there is a change to a value of a property, the dom element binded to that property will automatically update
- To handle an event, we need to bind that method with the DOM
- The reason DOM is de coupled, is because it makes our components unit testable

### Services
- To communicate with back end APIs like node or asp.net, we delegate any task that is not related to a view to services.
- Services is just a plain class that encapsulates and non-user interface logic like making http calls, logging, etc.

### Router
- The router is purely responsible for navigation
- For example, as a user scrolls, the router will decide what to display based on changes in the url

### Directives
- Directives are used to work this the DOM
- Unlike the component, a directive doesn't have a template or html markup for a view
- Directives are often used to add behaviour to existing DOM elements
- For example, with directives we can make a text box automatically grow when it is clicked on and is recieving input
- Angular comes with common pre built directives for common tasks like adding or removing DOM elements, adding classes or styles to them, repeating them, etc..
- Directives can also be custom made

Here is what a component would look like as code. Each component has data, and methods which describe the behaviour of the component{: .notice}
{% highlight javascript %}
export class RatingComponent{
  averageRating: number;
  setRating(value){

  }
}
{% endhighlight %}

**Note: npm is used to handle dependencies of our application**
