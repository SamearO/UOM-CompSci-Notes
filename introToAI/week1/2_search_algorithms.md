# Tree Search Algorithms

## Depth First Search
Comprehensively searches through a Tree by reaching the lowest point of a given path before searching the rest of the paths.

* It is not `complete` as it will endlessly try to compute a branch in an infinite tree. 
* It is not `optimal` as it can return a path that is longer than required in a graph.
* It has a small `space complexity` as it only needs to store the current path. 
* DFS can be used in infinite spaces if a `depth limited` search is used but it is still incomplete if the solution lies at a deeper depth than the parameter set by the `depth limit`.

### Using a Stack
```python
stack = Stack(root)

def dfs(queue):
    if len(queue) != 0:
        node = stack.pop()
        if desired_property(node):
            return node
        for child in node.children:
            stack.push(child)
        return dfs(queue)
    return False # Could not find a goal node 

```

### Using Recursion

```python
def dfs(root):
    if root is None:
        return False
    if desired_property(node):
        return node
    else:
        for child in node.children:
            dfs(child)
    return False
```

## Breadth First Search

BFS searches a Tree by searching through all nodes at the same level before progressing to the next level. Same implementation as `DFS` except it uses a `queue` instead of a `stack.

* It is `complete` as it searches through all node of the same level before progressing to the next level.
* It is not `optimal` as it can return a path that is longer than required in a graph. That being said, it is `optimal` if the path cost is a non-decreasing function of the depth of the node.
* It has a very large `space complexity` as the total number of nodes to store in the queue is b^d where b is the amount of successors per node and d is the depth.


# Heuristic Search Algorithms

Heuristic search algorithms use additional cost parameters to return a solution with a minimal cost as well as reducing the amount that a search space needs to be searched to find a solution.

## Heuristic assumptions
* Assume that each action has a non-negative cost, then each node will have a cost so far, annotated as `C(v)`
* Assume that each situation has a non-negative lower bound of cost to achieve the goal, hence each node has an underestimate of remaining cost `U(v)`. Eg the straight line distance between a starting point and its destination.
* We can use `K(v)` = `C(v)` + `U(v)` to get how `good` a node is based on the cost to get to the node and the estimate of the cost to reach the destination. 
* Any node with a higher `K(v)` is worse than a node with a lower `K(v)` hence any nodes encountered with a higher `K(v)` can be ignored. 
* Furthermore, since all costs are non-negative, we can ignore all children of the 
aforementioned nodes.

## Branch and Bound Search

```python
current_best = None
def bnb(stack, best_cost): # Queue initially has root node and best cost is infinity
    if len(stack) != 0:
        node = stack.pop()
        if K(node) < best_cost:
            if desired_property(node):
                current_best = node
                best_cost = K(node)
            else:
                for child in node.children:
                    stack.push(child)
    elif best_cost != float('inf'):
        return current_best
    else:
        return False # No path found 


```

## A* Search

Same as BNB but the stack is reordered every time a node is searched through. Every time a goal is found, it is `guaranteed` to be the least cost solution.

* It is `optimal` as it returns the least cost solution. It is optimal in the case where the heuristic never overestimates the cost to reach the goal.
* It is `complete` as it searches through all viable paths.
* It has a very large `space complexity` as it runs into the same queue issues as Breadth First Search.

```python
def ast(stack):
    if len(stack) != 0:
        node = stack.pop()
        if desired_property(node):
            return node
        else:
            for child in node.children():
                stack.push(child)
        
        stack.sort()
        return ast(stack)

    return False
```