**computable**: given [[hardware/PUFs/_PUFs - Physically Unclonable Functions|PUF]] and x, it is easy to evaluate $y =PUF(x)$ 
**reproducible**: $y \approx PUF(x)$ is reproducible, up to a *small error*

**unique**: $y$ contains some information about the identity of the physical entity embedding the PUF
**unclonable**: given PUF, it is hard to construct a procedure PUF' where $PUF(x) \approx PUF'(x)$ 
**unpredictable**: given a set of [[hardware/PUFs/Challenge-Response Pair CRP|CRPs]], it is hard to predict $y$
**one-way**: given only y and the corresponding PUF, it is hard to find x such that $y \approx PUF(x)$ 

**uniformity**: the number of 0 and 1 are equally distributed in a response
**repeatability**: the sets of CRPs should not change in time. (but PUFs are affected by aging and environment)
**uniqueness**: is the strength evaluation between two devices. Using Hemming Distance between 2 responses