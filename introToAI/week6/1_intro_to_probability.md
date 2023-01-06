# Introduction to Probability

## Degrees of Belief 

* Given a proposition that is unknown eg "it will rain tomorrow" and a ticket that costs 1 unit where the prize is 1 if the proposition is true and 0 otherwise.
* A degree of belief is the price an agent considers fair for purchasing the ticket.

## Synchronic Dutch Books

A dutch book is a sequence of bets of which the agent is disposed to take given their beliefs that together will cause the agent to lose money no matter what happens. This occurs when the agent's degrees of beliefs are not a probability assignment. (eg if the agent calculates propositions such as A and B incorrectly).

## Probability Assignments

The basic rules of a probability assignment `p(φ)`:
* If the proposition A is always True then `p(A) = 1`.
* If the proposition A and proposition B are mutually exclusive then `P(A or B) = P(A) + P(B)`.
* Thus if proposition A and proposition B are not mutually exclusive:
    * `P(A or B) = P(A) + P(B) - P(A AND B)`

## Conditional Probabilities

* Consider a conditional ticket:
    * 1 if A and B
    * 0 if not(A) and B
    * Money back if not(B)
    * Thus the fair price for this ticket is conditional amount aka `P(A|B)`.
* This can be broken down into 2 non-conditional tickets:
    * 1 if A and B, 0 otherwise.
        * The fair price for this ticket would thus be `P(A and B)`.
    * How much you paid for the ticket (amount_paid) if not(B), 0 otherwise.
        * The fair price for this ticket would thus be `amount_paid * P(not(B))`
* In all cases, the money earned/lost from the conditional ticket and the sum of the unconditional tickets are the same.
* By equating both sides we get:
* `P (A | B) = P(A and B)/P(B)`

## Bayes Theorem
* `P(A|B) = (P(B|A).P(A))/P(B)`

## Diochronic Dutch Book Argument

TODO figure this out because present me has no idea what Ian is talking about

## Bayesian Updating
* Using the above bayesian theorem, we can update our situation based on new information.
* Using the following variables, what is the probability of having covid if a test results in a positive result?:
    * Probability of a random person having covid: 0.001
    * Likelihood of the test being positive if you have the disease: 0.99, 0.01 if you don't.
* Let A be the probability of having the disease, and B be the event where the test was positive.
* Thus:
    * `P(B|A) = 0.99`
    * `P(A) = 0.001`
    * `P(B) = P(B|A)*P(A) + (1-P(B|A))*P(not(A)) = 0.01098`
* Finally, `P(A|B) = 0.09`
* In the case that a second test was done, replace the prior, `P(A)` with the result 0.09.

