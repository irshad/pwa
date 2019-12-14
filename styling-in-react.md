# Styling in React JS
![React](https://www.valuecoders.com/blog/wp-content/uploads/2016/08/react-1024x576.png)

## Inline Styling

Inline styles are nothing new,they are a HTML feature that we've all most likely used at some point. However,implementing inline styles in React is
slightly different,we store the values as objects.
### Inline object definition
```
<div style={{backgroundColor: "green" }}> IRSHAD ALI </div>
```
### Object literal definition
```
const divStyle = {backgroundColor: "green" }
<div sstyle={divStyle}> IRSHAD ALI </div>
```
Whilst inline style are often used when applying conditional style, they are often not the best choice when more than one element requires the same
styling.
### CSS & CSS Pre-processors
Whilst the process of using vanilla CSS or a CSS pre-processor is the same in React, there are a couple of notable differences. When applying
classes to elements, we use the 'className' syntax rather then 'class'. We also link our stylesheet using the @import syntax.
### For CSS
```
import React from 'react'
import './App.css'

const App = () => {
  return <Dogs/>
  }
export default App;
```
### CSS Modules
CSS Modules are simply `.css` file in which all CSS style and animation are defined. With an exception all of the style declared are locally
scoped to the Component they are imported into.
```
.dogSounds{
font-size: 1.5rem;
color: green;
text-decoration: underline;
}
```
All CSS style for one component are declared in one file.
```
import React from 'react'
import style form "./dog.css";

const Dog = () => {
  return <h1 style={style.dogSounds}> woof</h1>
}

export default Dog;
```
## CSS-in-JS Libraries
CSS-in-JS and inline style are extremely similar. However with inline styles React attaches the style to the DOM nodes,where as CSS-IN-JS libraries
 take your styles and inject them into a `<style>` tag in the DOM.
 ```
npm install --save styled-components
```
Can also b declared in another file and impored in
```
import styled from 'styled-components

const Title = styled,h1`
  font-size: 1.5em;
  color: green;
  text-align: center;
  `;
  
  **//IN COMPONENT**
```  
```
  <Title>
    Heloo World!
  </Title>
```
#### Thank's To @TheTraveling.Dev
