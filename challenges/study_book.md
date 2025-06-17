# Study book - challenges

This year's challenge classes will focus on the correct use of HTML structural elements, mobile-first design with TailwindCSS, and utilizing an API with Asynchronous JavaScript (AJAX).

## Learning goals

- The student uses modern web techniques (HTML and Tailwind) to implement a design that functions correctly on all browsers and consumes data from an API.

## The final assignment

You will implement a design for a simple web application that utilizes web services through a RESTful API.

Steps to successfully finish this assignment

1. **Choose API and create a simple design**
- [ ]  Choose your own API (everyone needs to have a unique API)
- [ ]  Create a design (for example in Figma) you want to implement using your API
- [ ]  Hand in your design and API of choice

**Guidelines for the design.**

- Do not make it to complex
- Mobile first is important: however you need to design a dekstop variant as well.
- There is at least one details page that can be accessed via a click on the home page
- All pages have relevant data that comes from the API
- The design should be different than the design used in the classes and unique compared to other students
- For mobile and web: at least one overview and one details page

1. **Delivering the design**
- [ ]  Implement the design
- [ ]  Zip the project (use .zip and **not** .rar or another exotic extension)
- [ ]  Host the project (for example on render.com)
- [ ]  Hand in the link to the hosted solution and the zipped code on learn

## Grading

If you want your project to be graded, you have meet the next conditions

1. API and Design are approved
2. The original (approved) design is implemented
3. Code is handed in as a zipfile. (use .zip and **not** .rar or another exotic extension)
4. A working example of the code is available for testing purpose (= deployed)

**Rubric**

For each criteria you will be given 0 or all points.

| **Part**        | **HTML**                                                                                         | **CSS layout**                                                                               | **CSS mobile first**                                                      | **AJAX requests**                                                             | **Concurrent AJAX requests**                                              |
| --------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| **Points (40)** | **8**                                                                                            | **4**                                                                                        | **4**                                                                     | **20**                                                                        | **4**                                                                     |
| **Do’s**        | Use of structural elements, like `<section>`, `<nav>` and `<aside>`                              | Use of `flexbox` and or `grid` for positioning                                               | Use of the Tailwindcss mobile approach (e.g. add `sm:` etc before classes | Use `fetch` or `async` `await` for fetching data from an external web service | `Promise.all()` or an equivalent is used for handling concurrent requests |
| **Don’t**       | I will pay attention to the amount of `<span>` and `<div>` that can be changed to other elements | I will pay attention to the amount of `<br/>`, `px` and or misuse of `padding` and `margin`. | Too many breakpoints are added                                            | Not handling `errors` correctly                                               | You didn’t implement concurrent requests                                  |

### Classes

| Class | Topic                        |
| ----- | ---------------------------- |
| 1     | HTML structural elements     |
| 2     | CSS with Tailwind            |
| 3     | AJAX and working with an API |
| 4     | Concurrent requests          |

