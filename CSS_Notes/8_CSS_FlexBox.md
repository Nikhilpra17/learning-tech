### CSS Flexbox Fundamentals - Important Notes & Examples

#### 1. **Flex Container and Flex Items**
   - **Flexbox** is used to align items in a flexible way, allowing them to be distributed either horizontally or vertically.
   - A container becomes a **flex container** when you apply `display: flex;` to it. Its child elements automatically become **flex items**.
   
   ```css
   .container {
     display: flex;
   }
   ```

   - **Result**: The child elements are aligned in a row (default behavior).

#### 2. **Flex Direction**
   - The **default direction** of flex items is a **row**.
   - Use `flex-direction` to control the layout direction:
     - `row`: Aligns items horizontally.
     - `column`: Stacks items vertically.
     - `row-reverse`: Reverses the order horizontally.
     - `column-reverse`: Reverses the order vertically.

   ```css
   .container {
     flex-direction: column;
   }
   ```

   - **Result**: Items are now stacked vertically.

#### 3. **Justify Content (Aligning Items Horizontally)**
   - Use `justify-content` to align items **horizontally**.
     - `flex-start`: Items align to the left.
     - `flex-end`: Items align to the right.
     - `center`: Items align in the center.
     - `space-between`: Even space between items, none at edges.
     - `space-around`: Even space between items, with a bit at edges.
     - `space-evenly`: Equal space between items and at edges.

   ```css
   .container {
     justify-content: space-between;
   }
   ```

   - **Result**: Items are spaced with equal gaps between them, no space on the edges.

#### 4. **Align Items (Aligning Vertically)**
   - Use `align-items` to align items **vertically** (cross-axis).
     - `flex-start`: Items align at the top.
     - `flex-end`: Items align at the bottom.
     - `center`: Items align in the middle.

   ```css
   .container {
     align-items: center;
   }
   ```

   - **Result**: Items are centered vertically.

#### 5. **Gap Property**
   - Use `gap` to add space between flex items. Works horizontally and vertically.

   ```css
   .container {
     gap: 1rem;
   }
   ```

   - **Result**: 1rem space between items.

#### 6. **Flex Wrap**
   - Use `flex-wrap` to control whether items wrap onto multiple lines if they overflow the container.
     - `nowrap`: Default, no wrapping.
     - `wrap`: Items will wrap onto multiple lines.

   ```css
   .container {
     flex-wrap: wrap;
   }
   ```

   - **Result**: Items wrap to new rows when they exceed the container width.

#### 7. **Align Content (Aligning Rows)**
   - Use `align-content` to align **rows** when there's extra space on the cross-axis.
     - `flex-start`: Rows are packed at the top.
     - `flex-end`: Rows are packed at the bottom.
     - `center`: Rows are centered.
     - `space-between`: Rows are evenly spaced.
     - `space-around`: Rows have space around them.
     - `space-evenly`: Equal space between rows and at the container edges.

   ```css
   .container {
     align-content: space-evenly;
   }
   ```

   - **Result**: Rows are evenly spaced within the container.

#### 8. **Flex Basis**
   - The `flex-basis` property sets the **default size** of an element before extra space is distributed.

   ```css
   .item {
     flex-basis: 100px;
   }
   ```

   - **Result**: Each item is at least 100px wide.

#### 9. **Flex Grow**
   - `flex-grow` allows items to **grow** to fill up the available space. The value represents the growth factor.
     - If two elements have `flex-grow: 1;`, they will grow equally.
     - If one element has `flex-grow: 2;`, it will grow twice as much.

   ```css
   .item1 {
     flex-grow: 1;
   }
   .item2 {
     flex-grow: 2;
   }
   ```

   - **Result**: `item2` will grow more than `item1`.

#### 10. **Flex Shrink**
   - `flex-shrink` allows items to **shrink** when there’s not enough space.
     - Items with a higher `flex-shrink` value shrink more than those with a lower value.

   ```css
   .item1 {
     flex-shrink: 1;
   }
   .item2 {
     flex-shrink: 2;
   }
   ```

   - **Result**: `item2` will shrink faster than `item1`.

#### 11. **Flex Shorthand**
   - The `flex` property is a shorthand for `flex-grow`, `flex-shrink`, and `flex-basis`.

   ```css
   .item {
     flex: 1 1 100px;  /* flex-grow flex-shrink flex-basis */
   }
   ```

   - **Result**: Item can grow, shrink, and has a base size of 100px.

#### 12. **Order**
   - Use the `order` property to change the **visual order** of flex items. The default is `order: 0;`.
     - Negative values move items earlier in the order.
     - Higher values move items later.

   ```css
   .item {
     order: 1;
   }
   ```

   - **Result**: This item appears after others with a lower order value.

---

### Example Flexbox Layout:

```html
<div class="container">
  <div class="box">1</div>
  <div class="box">2</div>
  <div class="box">3</div>
  <div class="box">4</div>
</div>
```

```css
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}

.box {
  flex: 1 1 150px; /* Grow, Shrink, and Basis */
  height: 100px;
  background-color: black;
  color: white;
  text-align: center;
  line-height: 100px; /* Vertical centering */
}
```

This code creates a responsive flexbox layout with gaps between items, ensuring they grow and shrink based on the container’s available space.
