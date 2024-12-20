# Accessibility Testing

Web accessibility is the inclusive practice of ensuring that websites, tools, and technologies are designed and developed so that people with disabilities (hearing, visual, motor disabilities etc.) can use them. It means that everyone, regardless of their abilities, can perceive, understand, navigate, and interact with the web.

## Important aspects of "Accessibility"

1. <ins>**Keyboard Navigation**</ins> – Users must be able to navigate the website just by using the keyboard, helpful for those who have difficulty in using the mouse.
    - In this [example](https://vishwac09.github.io/web-a11y-guidelines/keyboard-accessibility/correct/index.html) the site is fully traversible using the key board. Verify if you can visit all the visible / interactive elements of the site just by pressing the TAB key.
    - In this [example](https://vishwac09.github.io/web-a11y-guidelines/keyboard-accessibility/incorrect/index.html) the user is unable to interact with all the visible elements on the page.

2. <ins>**Using correct HTML elements**</ins> – Preserve the semantics of the HTML document. That is if you need to add a link use the "anchor" (&lt;a&gt;) element, instead of styling a paragraph (&lt;p&gt;) with css and adding an "onClick" handler to it.

    - Use proper elements to represent the correct click action.

      <ins>**Incorrect**</ins>
      ```html
      <p style="styled-button" onClick="() => clickHandler();">
        Click Me
      </p>
      ```
      <ins>**Correct**</ins>
      ```html
      <button style="styled-button" onClick="() => clickHandler();">
        Click Me
      </button>
      ```

    - Links must be represented using anchor links.
    
      <ins>**Incorrect**</ins>
      ```html
      <p style="styled-link" onClick="() => clickHandler();">
        Goto Home
      </p>
      ```
      <ins>**Correct**</ins>
      ```html
      <a href="/home" style="styled-link">
        Goto Home
      </a>
      ```

    - Use &lt;h1&gt;, &lt;h2&gt;, &lt;h3&gt; tags as page headings instead of using &lt;p&gt; tag with a styled font.

      <ins>**Incorrect**</ins>
      ```html
      <p style="styled-heading">
        Hello World
      </p>
      ```
      <ins>**Correct**</ins>
      ```html
      <h1>Hello World</h1>
      <h2>More Hello World</h2>
      ```

3. <ins>**Include Aria-tags whenever possible**</ins> – These tags are read by the screen-readers and other assistive tools to inform the user the purpose of the selected/focused element. Screen readers read the text currently visible on the screen or any other section that is focused by the user. Users having visual impairments usually use screen readers to understand the application flow. 

    ### Aria Tags <sub>(list of common and frequently used aria tags)</sub>

    - **aria-disabled** - The aria-disabled state indicates that the element is perceivable but   disabled, so it is not editable or otherwise operable.<br>
      <ins>**Usage**</ins>
      ```html
      <label for="user-age">Enter the age!</label>
      <input type="textfield" aria-disabled="false" name="age" value="" id="user-age" />
      <!-- acceptable values true/false/mixed -->
      <!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-disabled -->
      ```
    - **aria-expanded** - The aria-expanded attribute is set on an element to indicate if a control is expanded or collapsed, and whether or not the controlled elements are displayed or hidden.<br>
      <ins>**Usage**</ins>
      ```html
      <div class="menu-wrapper">
        <button aria-haspopup="true" aria-expanded="true/false" onClick="open the below menu">
            Sports
        </button>
      </div>
      <ul id="menu">
        <li>Cricket</li>
        <li>Football</li>
      </ul>
      <!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-expanded -->
      ```
    - **aria-haspopup** - The aria-haspopup attribute indicates the availability and type of interactive popup element that can be triggered by the element on which the attribute is set.<br>
      <ins>**Usage**</ins>
      ```html
      <div class="form-register">
        <input type="textfield" aria-disabled="false" name="birthday" value="" id="birthday" />
        <!-- calendar icon -->
        <img src="calendar-icon" onClick="toggle calendar" aria-haspopup="true"/> 
      </div>
      <div id="calendar"></div>
      <!-- When the focus is on the calendar image, the has popup aria tags will inform the user that clicking the lement opens a new popup window. -->
      <!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-haspopup -->
      ```
    - **aria-hidden** - The aria-hidden state indicates whether the element is exposed to an  accessibility API.<br>
      <ins>**Usage**</ins>
      ```html
      <button>
        <!-- Screen reader ignores the following element -->
        <span class="fa fa-tweet" aria-hidden="true"></span>
        <span class="label"> Tweet </span>
      </button>
      <!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-hidden -->
      ```
    - **aria-label** - The aria-label attribute defines a string value that can be used to name an element, as long as the element's role does not prohibit naming.<br>
      <ins>**Usage**</ins>
      ```html
      <button id="register-from-submit" aria-label="Submits the register form.">
        Submit
      </button>
      <!-- The screen reader will read the text inside the aria-label attribute, and ignore the button value shown on UI -->
      <!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label -->
      ```
    - **aria-labelledby** - The aria-labelledby attribute identifies the element (or elements) that labels the element it is applied to.<br>
      <ins>**Usage**</ins>
      ```html
      <button aria-label="Blue" aria-labelledby="color">Red</button>
      <span id="color">Yellow</span>
      <!-- When focused the above button, the screen reader will read the the button as Yellow -->
      <!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-labelledby -->
      ```
    - **aria-level** - The aria-level attribute defines the hierarchical level of an element within a structure.<br>
      <ins>**Usage**</ins>
      ```html
      <div role="heading" aria-level="3">Heading for this sub section</div>
      <!-- Treat the above div elemet as a Heading element with level 3 -->
      <!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-level -->
      ```
    - **aria-live** - The global aria-live attribute indicates that an element will be updated, and describes the types of updates the user agents, assistive technologies, and user can expect from the live region.<br>
      <ins>**Usage**</ins>
      ```html
      <body>
        <div class="modal" id="modal"  aria-live="polite">
          This is a modal. When the modal is shows to the user the screen reder must
          focus on the modal to read the contents of that modal.
        </div>
      </body>
      <!-- Treat the above div elemet as a Heading element with level 3 -->
      <!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-live -->
      ```
    - **aria-pressed** - The aria-pressed attribute indicates the current "pressed" state of a toggle button.<br>
      <ins>**Usage**</ins>
      ```html
      <div class="form-register">
        <input type="textfield" aria-disabled="true" name="birthday" value="" id="birthday" />
        <!-- calendar icon -->
        <img src="calendar-icon" aria-pressed="true" onClick="toggle calendar" aria-haspopup="true"/> 
      </div>
      <div id="calendar"></div>
      <!-- When the focus is on the calendar image, the has popup aria tags will inform the user that clicking the lement opens a new popup window. -->
      <!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-pressed -->
      ```
    - **aria-modal** - The aria-modal attribute indicates whether an element is modal when displayed. <br>
    <ins>**Usage**</ins>
      ```html
      <div id="backdrop" class="no-scroll">
        <div
          role="alertdialog"
          aria-modal="true"
          aria-labelledby="dialog_label"
          aria-describedby="dialog_desc">
          <h2 id="dialog_label">Confirmation</h2>
          <div id="dialog_desc">
            <p>Are you sure you want to delete this file?</p>
          </div>
          <button type="button" onclick="closeDialog(this)">
            No. Close this popup.
          </button>
          <button type="button" onclick="deleteFile(this)">
            Yes. Delete the file.
          </button>
        </div>
      </div>
      <!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-modal -->
      ```
    - **aria-required** - The aria-required attribute indicates that user input is required on the element before a form may be submitted.<br>
    <ins>**Usage**</ins>
      ```html
        <form id="user-regsiter" action="/register">
          <label for="first-name">First name*</label>
          <input type="text" id="first-name" name="firstName" aria-required="true">
          <label for="last-name">Last name*</label>
          <input type="text" id="last-name" name="lastName" aria-required="true">
          <label for="nick-name">Nick name</label>
          <input type="text" id="nick-name" name="nickName">
          <label for="email">Email*</label>
          <input type="text" id="email" name="email" aria-require="true">
        </form>
      ```
    - **aria-invalid** - The aria-invalid state indicates the entered value does not conform to the format expected by the application.
      <ins>**Usage**</ins>
      ```html
        <script type="text/javascript">
          function checkValidity(id, searchTerm, msg) {
            const elem = document.getElementById(id);
            if (elem.value.includes(searchTerm)) {
              elem.setAttribute("aria-invalid", "false");
              updateAlert();
            } else {
              elem.setAttribute("aria-invalid", "true");
              updateAlert(msg);
            }
          }
        </script>
        <form id="user-regsiter" action="/register">
          <label for="first-name">First name*</label>
          <input 
            type="text"
            id="first-name"
            name="firstName"
            aria-required="true"
            aria-invalid="false"
            onblur="checkValidity('first-name', ' ', 'Invalid name entered');"
            >
        </form>
      ```

4. <ins>**Measurement units**</ins> - Font sizes / Width / Heights must be referenced using rem as the unit, opposed to using pixels. Conversion 16px => 1rem. https://nekocalc.com/px-to-rem-converter.
    ```html
      <!-- # examples -->
      <p style="font-size: 1rem;">Hello world</p>
      <div style="width: 10rem;">
        Some content here
      </div>
    ```

5. <ins>**Responsiveness**</ins> - Responsive web design is about creating web pages that look good on all devices!. A responsive web design will automatically adjust for different screen sizes and viewports.
    ```css
    // X-Small devices (portrait phones, less than 576px)
    // No media query for `xs` since this is the default in Bootstrap

    // Small devices (landscape phones, 576px and up)
    @media (min-width: 576px) { ... }

    // Medium devices (tablets, 768px and up)
    @media (min-width: 768px) { ... }

    // Large devices (desktops, 992px and up)
    @media (min-width: 992px) { ... }

    // X-Large devices (large desktops, 1200px and up)
    @media (min-width: 1200px) { ... }

    // XX-Large devices (larger desktops, 1400px and up)
    @media (min-width: 1400px) { ... }
    ```

6. <ins>**Color**</ins> - Choosing the right color combination / contrast ratio - responsibility of the design team. 

By making websites accessible, we can create a more inclusive and equitable digital world for everyone. 
