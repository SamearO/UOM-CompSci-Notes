# Reducing CSP Search Spaces
* Search algorithms for finding a solution for CSPs can be sped up if the search space was smaller.

## Arc Consistency
* A variable is arc consistent if every value in its domain is valid for the constraints placed on the variable.
* A network is arc consistent if every variable in the network is arc-consistent with every other variable. (There is a solution to the CSP for every value in every variables domain).
* Arc consistency algorithms can be used to reduce the domain for the variables, reducing the search space. 
* If each variable only has 1 value in their domain after the algo, that is the solution.

```python
def AC3(csp):
    """
    AC3 is used to reduce the domain of all variables in the CSP such that only arc consistent values remain.
    """
    queue = csp.arcs
    while len(queue) > 0:
        x_1, x_2 = queue.pop()
        if revise(csp, x_1, x_2):
            if len(x_1.domain) == 0:
                return False # There are no solutions to this CSP
            for x in x_1.neighbours:
                if x != x_2:
                    queue.push(x, x_1)
    return True

def revise(csp, x_1, x_2):
    """
    Revise is used in AC3 to reduce the domain of x_1 such that it is arc consistent with x_2.
    Returns True if any changes to the domain were made, False otherwise.
    """
    revised = False
    for value_1 in x_1.domain:
        for value_2 in x_2.domain:
            if valid(value, value_2):
                break
        else:   
            # delete if there is no valid value in x_2
            # to satisfy constraint between x_1 and x_2
            x_1.delete(value_1)
            revised = True
    return revise
```

## Path Consistency
* Path consistency is like arc consistency but with 3 variables.
* Path consistency ensures that for every assignment on the first 2 variables, the third variable has a value that satisfies the constraint between itself and either of the first 2 variables.  