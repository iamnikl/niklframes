# Niklframes
## A simple serverless JavaScript Framework for building basic webpages using HTML, CSS and JavaScript.

- Lightweight
- Open-Source
- No Compiler
- No NodeJs needed
- All client-side
- Easy to integrate & use

## Basic Informations
NiklFrame is a lightweight and easy to use Framework developed for building standard client-side applications. 
This means that we do not use any compiler, instead we are working with simple JavaScript / TypeScript Classes. These Classes provide import methods, so you can import a file into another. The main purpose is working without using Frames, IFrames or hard-to-learn Frameworks using Server Side Code.

The whole project is open-source, so you can have a look in our Framework code. The code is online on GitHub.

## Installation
Install from Node Package Manager (npm):

```bash
npm install nikltools@latest
```

Create file system in your directory:

```bash
npm run template
```

*last is not required, but suggested

## Using Niklframes
To create a new Niklframes Project, start with creating a HTML Start file in the main repository. Now you can add the basic HTML Boilerplate code. When created, link the Framework JavaScript as an import in a script tag:
```html
<script>
  import { NiklComponent } from “../modules/niklframes/component.js“
</script>
```

This import statement imports the class called “NiklComponent“ which is used to add created components to your page.

## Components

### Creating a component
For creating a component, all you have to do is creating a new HTML File in the “components“ directory. A Niklframe component is build of basic HTML, but you mustn’t add the HTML boilerplate code.
A  NiklFrame component normally is saved with the file extension “.htm“, but you can change that using the App.d.js configuration file in your main root (here).
 
Here is an example of how a component can look like:

Header.htm

```html
<nav>
  <h1>Header</h1>
  <p>Welcome to my site</p>
</nav>
```

### Importing a component
Importing a component is an easy process, all you have to do is following these steps:

```html
<NiklComponent:Header />

<script>
  import { NiklComponent } from “../modules/niklframes/component.js“;
  let header = new NiklComponent(“header“);
</script>
```

As you can see, the NiklComponent class takes 1 argument, the name of your component. This is the filename of your component without the file extension “.htm“. 
As you already know, components are normally saved as .htm files, but you can specify this behaviour by configuring the “App.d.js“ file in your main directory. If you leave the value blank, you have to add the file extension manually in your NiklComponent componentName parameter.


### Component slots
Slots are a nice and easy way of making components flexible and variable. They can be placed as a placeholder in your component file and later be assigned with data in your route file. All you have to do is using the <slot name=““> Element at the place where you want the placeholder in your component file. Then, after filling out the slot name attribute value and importing the component to your route file, you can assign the placeholder with real value. To do that, you just have to add the slot attribute to your element, that should be used instead of the placeholder. The value of the slot attribute has to be exactly the same as the one you assigned in your component slot element (as name attribute).
Here is an example:

index.html (main File)
 ```html
<NiklComponent:Header>
  <span slot=“user-name“>Max</span>
</NiklComponent:Header>

<script>
  import { NiklComponent } from “../modules/niklframes/component.js“;
  let header = new NiklComponent(“header“);
</script>
```

Header.htm (component)
```html
<div>
  <h1>Hello <slot name=“user-name“></slot>! Nice to see you.</h1>
</div>
```

### Component Scripts
To make your Webpage dynamic, you use a programming language like JavaScript or TypeScript. But how are you able to write code for certain components?
For creating JavaScript Code for your Component, just add the <script> Element to your File.
This does not have any effect on how the code is executed, because when the Component is used, the script gets assigned to the route file‘s head area.

## Global variables
As you have maybe already noticed in the last example of slots, you sometimes need to use JavaScript to assign values to your HTML. To do this, you can use the build-in “setVariable()“ and “resolveVariable()“ method.
With setVariable, you can define a new global variable, which can be later used in the HTML.
Then you can use resolveVariable to make the value appear in the space you want to.
To set this space, all you have to do is adding curly brackets with the variable nam inside to your HTML Code. This will make the variable value appear.
Here is an example:


index.html (main File)
```html
<h1>Hello {username}</h1>
<script>
  import { NiklComponent } from “../modules/niklframes/component.js“;
  let header = new NiklComponent(“header“);
  header.setVariable(“username“, “Joe“);
</script>
```

Even though because of the header.setVariable it seems that this variable is only accessible in your Header Component. But this method only saves this variable in the Header Component Class.

You can also use these global variables in your component files:

Header.htm (Component)

```html
<p>This text is written for {username}.</p>
```

You don‘t need to import the username variable to your component file! This is done automatically by NiklFrame.

## Inline Scripts
Sometimes you might need to write down a JavaScript expression directly inside of your HTML build. That’s when you should take advantage of the build-in Inline Script Element.

You can use it by adding a new Element to HTML, called “<n-inline-js>“. Here you can type in any expression, even one that does not return a value. In this case, the code gets executed and the area containing the Element is left blank.

```html
Here is an example:
<p>
  <n-inline-js>7 + 3;</n-inline-js>
</p>
```
The HTML Code output would be:
```html
<p>10</p>
```

## NiklFrame Configuration
To configure certain behaviours, you can add these to the “NiklFrames.config.js“ file in your project root directory.
If you used the command “npm run template“, this file should already be existing in your directory.
Here are some features you can configure:

Component File Extentions:
```js
export const AppConfig = {
  components: {
    fileExtention: “.htm“
  }
}
```
You can specify the “fileExtention“ property by changing the default value of “.htm“ to any other file extension. We suggest you to use one of the following:
- .html
- .htm
- .xml
- .nik
- .nikl
- .txt
But you are free to chose what file extension you want to use for your components.
