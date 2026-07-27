
Motivation: find PK Family with shorter operands

Idea: can we find another [[crypto/cyclic groups|cyclic group]] in which the DLP is difficult? Ideally more difficult than in Zp?


$x^2 + y^2 = r^2$ and $ax^2 + by^2 = r^2$ equations over R (real numbers)

To use in crypto we need to consider polynomials over Zp


The EC over Zp, p > 3, is the set of all pairs (x,y) $\in$ Zp:
$$y^2 \equiv x^3 + ax+b \mod p$$
together with an imaginary point at infinity O, where a,b $\in$ Zp and 
$$4a^3 +27 b^2 \neq 0 \mod p $$

