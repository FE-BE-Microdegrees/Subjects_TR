# Creating Shapes with CSS

In this learning material, we explore how to use CSS to create various geometric shapes like squares, circles, and more. CSS provides simple ways to create these shapes, which can enhance the design of dynamic and visually appealing web pages.

## Learning Outcomes

After completing this topic, you will be able to:

- Create squares and circles using CSS;
- Use CSS to create more complex geometric shapes;
- Apply different CSS properties, such as `border-radius` and `clip-path`, to customize shapes.

## Squares and Rectangles

Creating squares and rectangles is simple as it only requires setting `width` and `height`. To create a square, set the width and height to the same value.

### Example: Square

```css
.square {
  width: 100px;
  height: 100px;
  background-color: #4CAF50;
}
```

### Example: Rectangle

```css
.rectangle {
  width: 200px;
  height: 100px;
  background-color: #f44336;
}
```

## Circles

To create a circle, use the `border-radius` property. Set the `border-radius` value to `50%` to make the element a circle.

### Example: Circle

```css
.circle {
  width: 100px;
  height: 100px;
  background-color: #008CBA;
  border-radius: 50%;
}
```

## Ovals

To create ovals, set different `width` and `height`  values and apply `border-radius: 50%;`.

### Example: Oval

```css
.oval {
  width: 150px;
  height: 100px;
  background-color: #e91e63;
  border-radius: 50%;
}
```

## Triangles

Triangles require creative use of the `border` property. Making parts of the `border` transparent creates the triangular effect.

### Example: Triangle

```css
.triangle {
  width: 0;
  height: 0;
  border-left: 50px solid transparent;
  border-right: 50px solid transparent;
  border-bottom: 100px solid #ff5722;
}
```

## More Complex Shapes with `clip-path` 

The CSS `clip-path` property allows for the creation of more complex shapes by defining a clipping area that determines the visible parts of an element.

### Example: Star Shape

```css
.star {
  width: 100px;
  height: 100px;
  background-color: #ffeb3b;
  clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
}
```

## Conclusion

CSS offers many options for creating various shapes, from simple geometric figures like circles and squares to more complex shapes like triangles and star-shaped objects. Mastering these techniques will help you design visually engaging web pages and improve user interface design. Experiment with these shapes to see how they can bring life to your web projects.
