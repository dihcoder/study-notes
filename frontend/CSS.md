# CSS Flexbox

## For Parent Element (The Container)

### Display
- `inline-flex` (the container will be inline)
- `flex` (container block)

### Flex-wrap
Defines whether the flex items should wrap or not.
- `nowrap` (default)
- `wrap` (if items don't fit on a single line)
- `wrap-reverse` (wrap with items in reverse order)

### Flex-direction (Horizontal axis by default)
- `row` (default), `row-reverse`, `column`, `column-reverse`

### Justify-content (Horizontal axis by default)
Aligns items along the main axis.
- `flex-start`, `flex-end`, `center`, `space-around`, `space-between`
- `start` (start of the writing mode direction)
- `end`

### Align-items (Vertical axis by default)
Aligns items along the cross axis.
- `flex-start`, `flex-end`, `center`

### Flex-flow (Combined property: flex-direction + flex-wrap)
Examples:
- `column wrap`
- `row-reverse nowrap`

### Align-content (Multiple lines property)
- `stretch` (lines stretch to fit the container)
- `flex-start`
- `flex-end`
- `center`
- `space-between`
- `space-around`

---

## For Child Elements

### Flex-basis
Defines the initial size of a flex item.
- `[size]` (e.g., `100px`, `50%`)

### Flex-grow & Flex-shrink
- `0` (The element doesn’t grow or shrink)
- Used with `flex-basis`, can serve as a starting point to grow or shrink.

### Flex (Shorthand for flex-grow + flex-shrink + flex-basis)
```css
flex: <flex-grow> <flex-shrink> <flex-basis>;
```
Example:
- `flex: 1;` (equivalent to `flex: 1 1 0`, meaning the item can grow, shrink, and are equal)

### Align-self (Vertical by default)
Overrides `align-items` for individual elements.
- `flex-start`
- `flex-end`
- `center`

### Order
Defines the order of elements.
- `[number]` (default value = `0`)

---

# CSS Grid

## For Parent Element (The Container)

### Display
- `grid`

### Grid-template-columns
Defines the number and size of columns.
Examples:
- `1fr 2fr;` (proportional sizing)
- `repeat(2, 200px);` (equivalent to `200px 200px`)
- `100px 200px;` (fixed sizes, not responsive)
- `100px auto;` (responsive, auto will take up the remaining space)
- `200px minmax(400px, 800px);` (limits for growing and shrinking)

### Grid-template-rows
Defines the number and size of rows.
Examples:
- `1fr 1fr;` (equal row heights)
- `200px 400px;` (fixed sizes, not responsive)
- `100px auto;` (row height fits content height)
- `repeat(3, 150px);` (three rows of `150px` each)

### Grid-template (Shorthand for grid-template-columns + grid-template-rows)
Example:
```css
1fr 2fr / 1fr 1fr;
```

### Grid-auto-rows
Defines row height for auto-generated rows.
```css
grid-auto-rows: 300px;  /* New rows will be 300px in height */
```

---

## For Child Elements

### Grid-column / Grid-row
Defines how many columns/rows an element will span.
Example:
```css
grid-column: span 2;  /* The item will use two columns */
```

### Grid-column-start, Grid-column-end, Grid-row-start, Grid-row-end
Specifies the exact start and end positions of an item.
Example:
```css
grid-column: 2 / 4;  /* Starts at line 2 and ends at line 4 */
```

### Dynamic End Position
When you don’t know how many columns exist, use `-1`.
Example:
```css
grid-column: 2 / -1;  /* Extends from column 2 to the last column */
```

