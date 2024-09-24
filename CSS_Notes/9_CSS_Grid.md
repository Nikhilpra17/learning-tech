### CSS Grid Layout - Key Points and Examples

#### 1. **Grid Basics**
- To create a grid layout, the container element should be defined as a grid by setting `display: grid`.
- All direct children of the grid container automatically become grid items.
  
#### Example:
```css
.container {
    display: grid;
}
```

#### 2. **Grid Auto Flow**
- **`grid-auto-flow`** determines how the grid items are placed in the grid.
  - **Row (default)**: Items fill in rows first.
  - **Column**: Items fill in columns first.

#### Example:
```css
.container {
    display: grid;
    grid-auto-flow: column; /* Items will be placed in columns */
}
```

#### 3. **Grid Template Columns**
- Use **`grid-template-columns`** to define the number and size of columns.
  - You can use absolute units like `px`, `em`, `rem`, or fractional units (`fr`) to allocate space proportionally.

#### Example 1 (Fixed sizes):
```css
.container {
    grid-template-columns: 200px 100px 200px;
}
```

#### Example 2 (Fractional units):
```css
.container {
    grid-template-columns: 2fr 1fr 1fr; /* First column is twice as big */
}
```

#### 4. **Using Repeat()**
- The **`repeat()`** function is a shorthand to avoid redundancy in defining multiple columns or rows with similar values.
  
#### Example:
```css
.container {
    grid-template-columns: repeat(4, 1fr); /* Four equal columns */
}
```

#### 5. **Grid Template Rows**
- Define the number and size of rows using **`grid-template-rows`** or use implicit row sizing with **`grid-auto-rows`**.
  
#### Example:
```css
.container {
    grid-template-rows: 100px 200px 100px;
}
```

- You can also use the **`minmax()`** function to define a range for the row height:
  
```css
.container {
    grid-auto-rows: minmax(150px, auto); /* Rows won’t shrink below 150px, but can grow */
}
```

#### 6. **Gaps**
- **`gap`** defines space (gutters) between grid items, and can apply to both rows and columns.
  - **`row-gap`** and **`column-gap`** can be used separately for rows and columns.
  
#### Example:
```css
.container {
    gap: 1rem; /* Applies to both rows and columns */
}
```

#### 7. **Grid Item Placement**
- Grid items can be positioned within the grid using **`grid-column-start`**, **`grid-column-end`**, **`grid-row-start`**, and **`grid-row-end`** properties.
- A shorthand version can be used with **`grid-column`** and **`grid-row`**.

#### Example:
```css
.item1 {
    grid-column: 1 / 4; /* Spans from column line 1 to column line 4 */
    grid-row: 1 / 3; /* Spans from row line 1 to row line 3 */
}
```

#### 8. **Shorthand for Grid Placement**
- Instead of specifying start and end separately, you can use a shorthand for rows and columns:
  
```css
.item1 {
    grid-column: 1 / 4;
    grid-row: 1 / 3;
}
```

#### 9. **Named Grid Areas**
- You can define specific areas of the grid by naming them using **`grid-template-areas`**.
  - Then, assign grid items to those areas using **`grid-area`**.

#### Example:
```css
.container {
    display: grid;
    grid-template-areas:
        "header header header"
        "main main sidebar"
        "footer footer footer";
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: auto auto auto;
}

.header {
    grid-area: header;
}

.main {
    grid-area: main;
}

.sidebar {
    grid-area: sidebar;
}

.footer {
    grid-area: footer;
}
```

#### 10. **Centering Content in Grid Items**
- Use **`place-content`** to center content inside grid items, combining **`align-content`** (vertical) and **`justify-content`** (horizontal).
  
#### Example:
```css
.item1 {
    display: grid;
    place-content: center;
}
```

#### 11. **Grid Inside Grid (Nested Grids)**
- You can create nested grids by making a grid item itself a grid container.
  
#### Example:
```css
.item1 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    place-content: center;
}
```

#### Summary
- **CSS Grid Layout** offers a flexible way to create two-dimensional layouts with both rows and columns.
- The key to mastering grids is understanding how to use **`grid-template-columns`**, **`grid-template-rows`**, **`gap`**, and placement properties effectively.
- Practice with tools like **Flexbox Froggy** and **Grid Garden** to gain hands-on experience!
