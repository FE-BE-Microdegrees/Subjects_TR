# CSS Borders

In this learning material, we explore the CSS `border` property, which allows developers to define borders around an element. Borders are used to visually outline elements, emphasize style, and enhance the distinctiveness of user interfaces.

## Learning Objectives

After completing this topic, you will be able to:

- Describe the use cases of the CSS `border` property;
- Define different `border` styles, widths, and colors;
- Apply and combine various `border` properties to create desired visual effects.

## What is the CSS Border Property?

The CSS `border` property allows developers to define borders for HTML elements. It is a shorthand property consisting of three main attributes: width (`border-width`), style (`border-style`), and color (`border-color`).

## Border Properties

The `border` property can be specified either as a shorthand or individually for each side:

- **`border-width`**: Specifies the border width (e.g., `px`, `em`, etc.).
- **`border-style`**: Specifies the border style (e.g., `solid`, `dashed`, `dotted`).
- **`border-color`**: Specifies the border color.

## Shorthand Property

Using the shorthand property, all three attributes can be set in a single declaration:

```css
div {
  border: 2px solid black;
}
```

## Different Border Styles

CSS offers various styles for borders:

- **`solid`**: A solid line.
- **`dotted`**: A dotted line.
- **`dashed`**: A dashed line.
- **`double`**: A double line.
- **`groove`**: A line with an inset effect.
- **`ridge`**: A line with an outset effect.
- **`inset`**: A line that appears pressed inward.
- **`outset`**: A line that appears pressed outward.
- **`none`**: No line is displayed.
- **`hidden`**: Hides the border.

## Border Width and Color

Border width and color can be specified independently:

```css
div {
  border-width: 5px;
  border-style: solid;
  border-color: blue;
}
```

## Styling Individual Sides

It is possible to style each side of the border separately using `border-top`, `border-right`, `border-bottom` and `border-left`:

```css
div {
  border-top: 2px dotted red;
  border-right: 3px solid blue;
  border-bottom: 4px dashed green;
  border-left: 5px double orange;
}
```

## Border-radius

The `border-radius` property allows corners to be rounded, creating oval shapes or rounded corners:

```css
div {
  border: 2px solid black;
  border-radius: 10px; /* Rounds all corners */
}
```

## Conclusion

The CSS `border` property is a powerful tool that enables developers to customize element boundaries in various ways. From simple borders to complex, multi-layered designs, border properties can enhance the aesthetics and usability of user interfaces. Practical experience with these properties will help developers create more visually appealing and functional web pages.
