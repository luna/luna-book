# Switching between representations

Luna delivers a mechanism for the two way translation between visual and textual representations. It allows you to switch the representation on demand and even work on both of them at the same time. The  implementation details are beyond the scope of this book, however, from the high perspective the translation is a straightforward process.

In the most common case, each Luna node corresponds to a line of code. For example:

![](assets/ex1.png)

```python
a = 1
b = 2
c = a + b
c.succ
```


Let's break this graph down:

1. The two leftmost nodes correspond to the lines `a = 1` and `b = 2`. The variable names `a` and `b` become names of their corresponding nodes, and the numbers `1` and `2` are their definitions. They have no input ports and one output port each.
2. The node in the middle corresponds to the line `c = a + b`. It has the `a` and `b` nodes connected to its inputs. Thanks to this, you can clearly see where does the input data come from.
3. The rightmost node corresponds to the line `c.succ`. The node has no name, as the corresponding line does not define any variables. It has the node `c` connected to its `self` port. This port denotes the target of method call.

