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
- In typescript you cannot change the type of a varibale
For example, say we have a variable
myVar = "a string"
unlike javascript we cannot assign it a different value of type int
myVar = 25
- We can declare the type of variable in tyepscript. Although we don't have to.  

{% highlight javascript %}
myVar:String = "hello"
myVar:number = 20
myVar:boolean = true
myVar:any
myVar = 50
myVar:number[]
{% endhighlight %}

- Typescript allows us to make classes

{% highlight javascript %}
class car{
  speed:number;
  constructor(mph:number){
    this.speed = mph;
  }
}

myCar:Car = new Car(79)

{% endhighlight %}


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

## component.ts file
- the import statement imports the component from the angular class
- Next up is the decorator defined by @Component{} and it defines more information about the class like how it works
- inside the decorator is something called selector, and is the name of the tag which the component and component view is loaded into
-  This file contains the logic

## component.html
- contains the html

## component.css
- contains the style sheet
- captain obvious!

## Directives
- Directives are something that tell angular  what to do

## creating a new component
- ng generate component componentName
- component has "implements OnInit", you can assign the component to do something on initialization
- to display a child component, you have to put the component tag in the component.html file of the root component
- in addition, to have the component display on site, you have to write an import statement in the home component.
- import { ComponentName } from './locationOfFile'

## ng content directive
- if you want to display content by putting it inside a tag such as <app-home></app-home> you can do so by using the ng content directive
- write <ng-content></ng-content> inside the component.html file

## data binding
- Passing data back and forward between component and template
- **String interpolation** {{stringName}}
- **event binding** allows data to flow out of view (HTML file) and into the class (typescript file) and bind events to Html elements
- **Two way data binding** allows data to flow both ways
- **Property Binding** <input[required]='expression'> binds expression to a HTML property
### Property Binding
- one way to property bind is by saying
{% highlight html %}
<input [value] = "nameOfProperty"/>
{% endhighlight %}
- Another way is to use string interpolation
{% highlight html %}
<input required = {{nameOfProperty}}/>
{% endhighlight %}

### event binding
- Binding native events suhc as click events
{% highlight html %}
<button (click)="function">
{% endhighlight %}
- Binding to custom events that we make
{% highlight html %}
<app-home (update)="function"></app-home>
{% endhighlight %}

## Two way data binding
- [(ngModel)]

## Sending data between two components
### /@Input
- if you want to pass data from root component to child component, you do it through the root components component.html file
- do this by binding what ever data you want in the tag referencing the child component
{% highlight html %}
<app-home [bindName]="propertyName">I like trains</app-home>
{% end highlight %}
- in addition you will have to use the input decorator, and add "input" in the import statement at the top of the component.ts file of the component you want to data to go to.
{% highlight html %}
@Input() bindName
{% end highlight %}

### /@Output
-

##index. html

<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>NinjaDirectory</title>
  <base href="/">

  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
  <app-root>Loading...</app-root>
</body>

	<script src="https://www.gstatic.com/firebasejs/3.6.6/firebase.js"></script>
	<script>
		// Initialize Firebase
		var config = {
			apiKey: "AIzaSyCx18R2crzYSXV8Sp0KsSy35I-FzuTTKME",
			authDomain: "nn-angular-3f5e8.firebaseapp.com",
			databaseURL: "https://nn-angular-3f5e8.firebaseio.com",
			storageBucket: "nn-angular-3f5e8.appspot.com",
			messagingSenderId: "941550239447"
		};
		firebase.initializeApp(config);
	</script>
</html>


## main .ts

import './polyfills.ts';

import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { enableProdMode } from '@angular/core';
import { environment } from './environments/environment';
import { AppModule } from './app/app.module';
import { LoggingService } from './app/logging.service';

if (environment.production) {
  enableProdMode();
}

platformBrowserDynamic().bootstrapModule(AppModule, [LoggingService]);


## ninja .json

[
  {
    "name":"Shaun",
    "belt":"black"
  },{
    "name": "Yoshi",
    "belt": "black"
  },{
    "name": "Ryu",
    "belt": "red"
  },{
    "name": "Crystal",
    "belt": "purple"
  }
]


## styles .css

body{
  font-family: verdana;
  letter-spacing: 0.1em;
  color: #606060;
  background: #eee;
  padding: 20px;
}

h1,h2,h3{
  font-weight: normal;
  margin-top: 0;
}

h1{
  text-indent: -10000px;
  background: url(logo.png) no-repeat center bottom;
  background-size: 100%;
  width: 140px;
  height: 100px;
  margin: 0 auto;
}

/* NAVBAR */

nav{
  width: 100%;
  max-width: 740px;
  margin: 0 auto;
}

nav ul{
  padding: 0 !important;
  background: #0288d1;
  display: flex;
  box-shadow: 0 1px 3px 0 rgba(0,0,0,0.2),0 1px 1px 0 rgba(0,0,0,0.14),0 2px 1px -1px rgba(0,0,0,0.12);
  border-radius: 2px;
  margin-top: 0;
}

nav li{
  flex-basis: 0;
  flex-grow: 1;
  list-style-type: none;
}

nav a{
  text-align: center;
  padding: 16px 0;
  color: #eee;
  display: block;
  text-decoration: none;
}

nav a:hover{
  background: #1298e1;
}

/* MAIN */

#main{
  background: #fdfdfd;
  padding: 20px;
  box-shadow: 0 1px 3px 0 rgba(0,0,0,0.2),0 1px 1px 0 rgba(0,0,0,0.14),0 2px 1px -1px rgba(0,0,0,0.12);
  border-radius: 2px;
  width: 100%;
  max-width: 740px;
  box-sizing: border-box;
  margin: 0 auto
}

#filter{
  padding: 12px;
  background: #e7e7e7;
  border-radius: 2px;
  line-height: 30px
}

#filter input{
  padding: 8px;
  width: 300px;
  border: 1px solid #d4d4d4;
  border-radius: 2px;
  float: right;
}

#filter:after{
  content: "";
  display: block;
  clear: both;
}

#ninja-listing li{
  padding: 16px 0;
  border-bottom: 1px solid #e4e4e4;
}

.single-ninja span{
  display: inline-block;
  border-radius: 2px;
  font-size: 14px;
  text-transform: uppercase;
  padding: 8px !important;
}

.single-ninja h3{
  padding: 4px;
  font-size: 20px;
  margin-left: 20px;
  display: inline-block;
}

.single-ninja div{
  float: right;
  margin-right: 10px;
  line-height: 20px;
  cursor: pointer;
}

#add-ninja{
  margin-top: 30px;
  background: #e7e7e7;
  padding: 10px;
  border-radius: 2px;
}

#add-ninja input{
  display: inline-block;
  padding: 10px;
  border-radius: 2px;
  border: 1px solid #ddd;
  width: 240px;
}

#add-ninja button{
  background: #0288d1;
  color: #eee;
  padding: 8px 10px;
  border: 0;
  borader-radius: 2px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  float: right;
}
