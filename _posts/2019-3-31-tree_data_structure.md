---
layout: post
title: Tree Data Structures
---

For those who are beggining the world of data structures, you will find a neat type of data structure called a tree. When you look for a
tree data structure, you will most commonly find an upside down tree with nodes or circles that point to two other nodes below themselves.
Although this might be the most common way to represent this type of data structure, it can look vastly different. For one, a tree has a root,
where the entire tree begins. Then, the root has branch or multiple branches, that stem out from the root. This repeats on and on for as long as possible until there is a node that points to a null.
Despite this, we commonly use a node that branches out to a maximum of 2 nodes. This is because the tree data structure is used mostly for its advantage to 


<pre>
                50
               /  \
             30     60
            /  \   /  \
          15   31  55  75
</pre>


```py
def bfs(node):
    if not node:
        return
    bfs(node.left)
    print(node.val)
    bfs(node.right)
```
