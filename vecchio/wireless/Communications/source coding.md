> **source coding** aims to represent data in a more **compact way**, in order to reduce redundancy and save storage space or transmission bandwidth


The primary goal is to **minimize redundancy**

There are different compression classes for source encoding:
- **loseless**, ensures that the original data can be perfectly reconstructed from compressed version (ZIP,PNG) 
- **lossy**, sacrifices some data accuracy for higher compression ratios (JPEG,MP3)

There is a trade-off between compression efficiency and computational complexity.

Lastly, **differential encoding** is the process of storing the information **about** **which part** of data **changed** and which not, therefore updating only the ones changed.