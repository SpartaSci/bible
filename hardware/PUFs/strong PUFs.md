>**Strong PUFs** have a large set of [[hardware/PUFs/Challenge-Response Pair CRP|CRP]] (>280). They are mostly used for **authentication** and some CRPs become public, the others still ensure secure.

However, if enough CRPs are collected, machine learning algorithms migh predict the output, which is less feasible with [[hardware/PUFs/weak PUFs|weak PUFs]]


The stability of the output is crucial to avoid errors, but errors help against ML attacks (the attacks is easier with stable output). For this, instead of just relying on one CRP, you try several

Arbiter PUFs is a Strong PUF, since the configuration is based on the multiplexer setup and provide a large space of CRPs

[[electronics/Ring oscillator|Ring oscillator]]


# IC authentication
![[hardware/PUFs/Challenge-Response Pair CRP|CRP]]


