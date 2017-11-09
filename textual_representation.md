#Textual representation

Luna is a data processing language and like every language it provides a syntax. However, in contrast to majority of languages Luna has more than one syntax representation – visual and textual. This chapter describes the later – the code.

Luna was designed to be a highly readable language. While designing its textual representation the main focused was put on creating a clean, concise yet expressive syntax.

## Code layout
Luna code is indentation sensitive, which means that logically nested expressions are also visually nested in code. The layout were designed to maximally increase code readability and layout flexibility. There are three rules describing how it works:

1. Each block could start in current or a new line. The block's indentation level is the same as it's first expression's indentation;
2. Each nested code block should have bigger indentation level than the parent's one;
3. Expressions can span over multiple lines, but all the spanned lines have to be indented more than the expression itself.

Luna does not allow mixing the use of tabs and spaces, only spaces are allowed for making code indentations. Almost every block starts with the colon `:` operator. Here are some examples of different usages of indentation layout. You do not have to understand the code yet, it's important however to feel how the layout works.

```ruby
# inline expression
def sum a b: a + b

# multiline expression:
def checkVector v:
    if v.x > v.y then True
                 else False

# standard function declaration with indented code block
def main:
    v = Vector 1 2 3
    print $ checkVector v
```

The following examples are **invalid**:

```ruby
# ERROR: Multiline expression is not properly indented
def checkVector v:
    if v.x > v.y then True
    else False

# ERROR: Indentation level does not match the first expression's one
def main: v = Vector 1 2 3
    print $ checkVector v
```


##Scoping
Scopes define when a particular name is accessible in a program. Each code block creates a distinct name scope, inheriting the names from the parent one. All the names of entities defined in a scope cannot escape its boundaries, in particular they cannot be accessed from the parent scope.

