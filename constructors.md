# Constructors and Pattern Matching

## Pattern matching

Pattern matching is a mechanism allowing to discover which particular constructor was used to create a given object. It also allows to bring the values of fields (even unnamed) of the constructor into the scope. Let's get back to the `Shape` example once again. Suppose you have facilities for rendering circles and rectangles and you need to render `Shape`s. This can be accomplished with a simple pattern match:

```
def render shape:
case shape of
Circle c r: renderCircle c r
Rectangle tl br: renderRectangle tl br
```