### Key Notes on CSS Columns (with examples)

1. **Creating Columns with CSS:**
   - You can use the `columns` property to divide content into multiple columns.
   - **Example:**
     ```css
     .columns {
       column-count: 4;
     }
     ```
   - This will split the content within the `.columns` class into 4 columns.

2. **Column Width:**
   - You can also control the minimum width of columns using `column-width`.
   - **Example:**
     ```css
     .columns {
       column-width: 250px;
     }
     ```
   - This ensures that the column width doesn't drop below 250px, even when resizing the browser. If the space allows more columns, it adjusts automatically.

3. **Shorthand for Columns:**
   - Instead of using `column-count` and `column-width` separately, you can combine them into a single shorthand property.
   - **Example:**
     ```css
     .columns {
       columns: 4 250px;
     }
     ```
   - This creates up to 4 columns with a minimum width of 250px.

4. **Adding Column Rules (Borders):**
   - The `column-rule` property is similar to using a border between columns.
   - **Example:**
     ```css
     .columns {
       column-rule: 3px solid black;
     }
     ```
   - This adds a 3px solid black divider between each column.

5. **Adjusting Spacing Between Columns:**
   - The `column-gap` property adds space between the columns.
   - **Example:**
     ```css
     .columns {
       column-gap: 3rem;
     }
     ```
   - This sets a gap of 3rem between columns, enhancing readability.

6. **Margin Collapsing:**
   - Margins between elements (like paragraphs) inside columns can collapse, meaning the space between them isn’t doubled even if both top and bottom margins are applied.
   - If you want to remove the top margin from the first paragraph in a column:
     ```css
     .columns p:first-of-type {
       margin-top: 0;
     }
     ```

7. **Handling Headings (H2) and Column Breaks:**
   - If you don’t want a heading to split across two columns, use the `break-inside` property to prevent awkward splits.
   - **Example:**
     ```css
     .columns h2 {
       break-inside: avoid;
     }
     ```
   - This keeps the heading in one column and prevents it from splitting across columns.

8. **Forcing Column Breaks:**
   - You can force a new column to start before a specific element using `break-before`.
   - **Example:**
     ```css
     h2 {
       break-before: column;
     }
     ```
   - This forces a new column to start before the heading, which is useful for layout control.

9. **Handling Special Content (Quotes, Highlighted Text):**
   - Use the `column-span` property to make content span across all columns.
   - **Example:**
     ```css
     .quote {
       column-span: all;
     }
     ```
   - This makes elements like quotes span across the entire column width, which is commonly used for emphasis.

10. **Dealing with Line Breaks in Text (No Wrap):**
    - Use `white-space: nowrap` to prevent text (like author names) from breaking awkwardly.
    - **Example:**
      ```css
      .no-wrap {
        white-space: nowrap;
      }
      ```
    - This ensures text like author attribution remains on a single line, even in tight spaces.

---

### Example Code Putting It All Together:

```html
<section class="columns">
  <h2>Next Topic</h2>
  <p>Lorem ipsum dolor sit amet.</p>
  <p>Consectetur adipiscing elit.</p>
  <p>Quisque vehicula magna.</p>
  <p>Aenean commodo ligula eget dolor.</p>
  <p class="quote">"Where's my rug?" — The Dude</p>
</section>
```

```css
body {
  font-family: 'Roboto', sans-serif;
  font-size: 1.5rem;
}

.columns {
  columns: 4 250px;
  column-gap: 3rem;
  column-rule: 3px solid black;
}

.columns p:first-of-type {
  margin-top: 0;
}

.columns h2 {
  break-inside: avoid;
  margin-top: 0;
  background-color: #333;
  color: #fff;
  padding: 1rem;
}

.quote {
  column-span: all;
  font-size: 3rem;
  text-align: center;
}

.no-wrap {
  white-space: nowrap;
}
```
