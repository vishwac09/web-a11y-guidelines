# Accessibility Testing

Web accessibility is the inclusive practice of ensuring that websites, tools, and technologies are designed and developed so that people with disabilities (hearing, visual, motor disabilities etc.) can use them. It means that everyone, regardless of their abilities, can perceive, understand, navigate, and interact with the web.

## Important aspects of "Accessibility"

1. <ins>**Keyboard Navigation**</ins> – Users must be able to navigate the website by using a keyboard, helpful for those users who have difficulty in using the mouse. To get more understanding of this point check out the examples below.
    - In this [example](https://vishwac09.github.io/web-a11y-guidelines/keyboard-accessibility/correct/index.html) the Site is fully traversible using a key board. See if you can use the site just by pressing the TAB key. [View](https://vishwac09.github.io/web-a11y-guidelines/keyboard-accessibility/correct/index.html)
    - In this [example](https://vishwac09.github.io/web-a11y-guidelines/keyboard-accessibility/incorrect/index.html) user is unable to interact with all the visible elements on the page. [View](https://vishwac09.github.io/web-a11y-guidelines/keyboard-accessibility/incorrect/index.html)

2. <ins>**Using correct HTML elements**</ins> – When developing the application always use correct HTML elements to serve the purpose. e.g.
    - Use proper elements to represent the correct click action.

      <ins>**Bad approach**</ins>
      ```html
      <p style="styled-button" onClick="() => clickHandler();">
        Click Me
      </p>
      ```
      <ins>**Good approach**</ins>
      ```html
      <button style="styled-button" onClick="() => clickHandler();">
        Click Me
      </button>
      ```

    - Links must be represented using anchor links.
    
      <ins>**Bad approach**</ins>
      ```html
      <p style="styled-link" onClick="() => clickHandler();">
        Goto Home
      </p>
      ```
      <ins>**Good approach**</ins>
      ```html
      <a href="/home" style="styled-link">
        Goto Home
      </a>
      ```

    - Use &lt;h1&gt;, &lt;h2&gt;, &lt;h3&gt; tags as page headings instead of using &lt;p&gt; tag with a styled font.

      <ins>**Bad approach**</ins>
      ```html
      <p style="styled-heading">
        Hello World
      </p>
      ```
      <ins>**Good approach**</ins>
      ```html
      <h1>Hello World</h1>
      <h2>More Hello World</h2>
      ```

3. <ins>**Include Aria-tags whenever possible**</ins> – These tags are read by the screen-readers and other assistive tools to inform the user the purpose of the selected/focused element. Screen readers read the text currently visible on the screen or any other section focused by the user. Users having visual impairments usually use screen readers to understand the application.  
    - Example: - Register form – How do inform the user if a field is required inside the form?  
    - Image ALT text - All images must have an alt text explaining what the image is.  

4. <ins>**Responsiveness**</ins> - Application must be responsive.  

5. <ins>**Color**</ins> - Choosing the right color combination / contrast – responsibility of the design team. 

6. <ins>**Measurement units**</ins> - Font sizes / Width / Heights must be referenced using rem as the unit, opposed to using pixels. Conversion 16px => 1rem. https://nekocalc.com/px-to-rem-converter  

By making websites accessible, we can create a more inclusive and equitable digital world for everyone. 

 