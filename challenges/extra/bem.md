
# BEM (Block Element Modifier)

If you're writing plain CSS or Sass for a medium to large project, BEM is still a best practice. But in modern toolchains with scoped or utility-based styling, BEM may be less necessary.

Why BEM is still relevant:
1. Scalability: BEM naming conventions help manage CSS in large projects by avoiding selector collisions.
2. Clarity: The structure (block__element--modifier) makes it immediately clear what a class is doing.
3. Tool Compatibility: Works well with vanilla CSS, Sass, Less, and even CSS-in-JS if desired.
4. Component-based architecture: Aligns well with modern frontend frameworks like React or Vue, which are also component-oriented.

Alternatives and Modern Context:
- CSS Modules: Scope styles automatically, reducing the need for BEM.
- Tailwind CSS: Uses utility classes, so BEM is largely unnecessary.
- Styled Components / Emotion: Encapsulate styles per component using JavaScript.

## Examples for the different strategies

A comparison using a simple button component in different CSS strategies: BEM, Tailwind CSS, CSS Modules, and Styled Components.

### 1. BEM

HTML
```HTML
<button class="button button--primary">Click me</button>
```
CSS
```CSS
.button {
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}

.button--primary {
  background-color: blue;
  color: white;
}

```

### 2. Tailwind CSS (Utility First)

HTML
```HTML
<button class="button button--primary">Click me</button>
```
- No custom CSS required — classes handle it all.
- Faster to write, but can get verbose or hard to manage without good conventions.

### 3. CSS Modules
Button.module.css
```CSS
.button {
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}

.primary {
  background-color: blue;
  color: white;
}
```
React component
```jsx
import styles from './Button.module.css';

<button className={`${styles.button} ${styles.primary}`}>Click me</button>
```

### 4. Styled Components (CSS-in-JS)
React Component:
```jsx
import styled from 'styled-components';

const Button = styled.button`
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  background-color: blue;
  color: white;
`;

<Button>Click me</Button>
```
- Styles are tied directly to components.
- Great for dynamic theming and conditional styles.