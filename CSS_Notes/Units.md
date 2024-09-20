CSS units are essential to defining the size of elements on a webpage. Here’s a summary of some commonly used CSS units:

### 1. **Pixels (px)**:
   - **Definition**: A fixed unit that represents a single pixel on the screen.
   - **Usage**: Often used for borders, images, or other elements where an absolute, fixed size is desired.
   - **Example**:
     ```css
     h1 {
       border: 2px dashed red;
     }
     ```
     This example gives the `h1` element a 2-pixel wide red dashed border.

### 2. **Percentages (%)**:
   - **Definition**: A relative unit based on the parent element’s size.
   - **Usage**: Commonly used to set width or height based on the size of the parent container.
   - **Example**:
     ```css
     h1 {
       width: 50%;
     }
     ```
     This example sets the width of the `h1` element to 50% of its parent element's width.

### 3. **Root em (rem)**:
   - **Definition**: A relative unit that references the root element’s font size (usually the default browser font size, typically 16px).
   - **Usage**: Best used for font sizes, allowing the entire layout to scale based on the root font size.
   - **Example**:
     ```css
     p {
       font-size: 2rem;
     }
     ```
     This sets the paragraph font size to double the root font size, making it 32px if the root size is 16px.

### 4. **em**:
   - **Definition**: A relative unit based on the font size of the element's parent.
   - **Usage**: Best used for padding and margins because it's relative to the element’s font size, allowing consistent spacing even if font sizes change.
   - **Example**:
     ```css
     h1 {
       padding: 1em;
     }
     ```
     This adds padding equal to the size of the font within the `h1` element.

   - **Warning**: Using `em` for font size can cause unintended amplification, especially when nested elements have different font sizes. It's recommended to use `rem` for fonts.

### 5. **Character Unit (ch)**:
   - **Definition**: A relative unit based on the width of the "0" (zero) character in the current font.
   - **Usage**: Ideal for setting widths of text containers to control the number of characters per line.
   - **Example**:
     ```css
     p {
       width: 40ch;
     }
     ```
     This sets the paragraph width to approximately 40 characters wide.

### 6. **Viewport Width (vw) & Viewport Height (vh)**:
   - **Definition**: Relative units based on the size of the viewport. 1vw is 1% of the viewport's width, and 1vh is 1% of the viewport's height.
   - **Usage**: Useful for responsive design, ensuring elements scale with the browser window size.
   - **Example**:
     ```css
     div {
       width: 50vw;
       height: 50vh;
     }
     ```
     This sets the width and height of a `div` to 50% of the viewport’s width and height.

### Resetting Default Styles:
Many browsers have default styles for elements, like margins and padding. A CSS reset ensures that elements behave consistently across browsers.

- **Example** of a simple CSS reset:
  ```css
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  ```

This removes all default margin and padding and sets `box-sizing` to `border-box`, which ensures that padding and border are included in the total width and height of elements.

### Conclusion:
Understanding CSS units is crucial to building flexible and responsive designs. Use `rem` for fonts, percentages for relative widths, and pixels for exact sizing (like borders). Combining these units effectively leads to adaptable layouts that respond well to user settings and different screen sizes.
