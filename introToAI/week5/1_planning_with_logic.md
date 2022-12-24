# Representing Planning with First Order Logic

* Planning problems can also be represented with first order logic, however:
    * It is slower to compute.
    * First order logic is more flexible in what it can represent.

## Representation using First Order Logic
* Actions and parts of situations can be represented by functions. Each action has a list of preconditions for the action to be taken.
* The constraints of the problem needs to be represented by a combination of actions and situations.
* Goals are represented by creating situations and the corresponding actions to get there, these actions will need to be derived by a theorem solver.

### Example Block World Actions
* `move(x,y,z)`: Moving x from y to z.
    * Preconditions for do(move(x,y,z), w): `clear(z,w) ^ clear(x, w) ^ x != z `
    * In all situations and with all blocks, if x is on y in situation w, and there is nothing on top of x or w in this situation, then when x is moved on z from y, x is on z and y is clear.
* `do(u,w)`: The situation produced by action u in situation w.

### Example Block World Situations
* `on(a,b,c)`: a is on b in situation c.
* `clear(a,s)`: a is clear (nothing is on top of it) in situation s.

## Representing The Block World Constraints
* `∀x∀y∀z∀w(on(x, y, w) ^ clear(x, w) ^ clear(z, w), ^ x != z -> on(x, z, do(move(x,y,z), w)) ^ clear(y, do(move(x,y,z), w)))`
* In all situations and with all blocks, if x is on y in situation w, and there is nothing on top of x or w in this situation, then when x is moved on z from y, x is on z and y is clear.
* Note that only positive effects were written down, if there were other blocks that were not affected, they did not show up in this statement. This suffices for a simple problem like block world but is required in more complex problems.

## Representing a Plan
* A plan can be represented by a series of actions eg move(a,b,table) then move(b,table, c) can be represented as:
* `do(move(b,table,c), do(move(a,b,table), s0))`
* Note that the second do argument for the second step is the do move of the first step, hence plans are made by chaining moves in a backwards manner all the way down to the initial situation `s0`.

## Representing a Goal
* Goals need to be represented using a situation and the steps taken to get to that situation.
* Eg: put a on b and b on c
* `on(a, b, do(move(a, table, b), do(move(b, table, c), do(move(a, b, table), s0))))` ^ `on(b, c, do(move(a, table, b), do(move(b, table, c), do(move(a, b, table), s0))))`
* Note that the moves are the same in both conditionals.

# Getting a Plan that satisfies the Goal
* The above representation of the goal is not very useful as we need the steps to get to the goal to even represent the goal. Hence it seems counterproductive to represent a goal in that manner when trying to find a plan to solve the goal.
* However, we can get a theorem solver to find the plan for us.
* A way to solve "there exists" statements is to find at least one plan that satisfies the statement.
* Hence, passing in `∃w(on(a,b,w) ^ on(b,c,w))` to a theorem solver along with our constraints will give us the plan required to represent the goal.