---
tags:
  - network
  - authorization
aliases:
  - IDS
---
> IDS is a system designed to identify actors using a computer or a network without #authorization 

IDS is based on a crucial hypothesis: **the behavioral pattern of non-authorized users differs from that of authorized ones**


IDS can base its behavior on two strategies
# passive IDS
> tries to identifies visible signs of an attack

cryptography checksum: checking for modified files on the server that should not be modified

Pattern matching: looking for specific patterns which are typical of an attack

# active IDS 
> tries to identify unknown attacks or known attack but before they produce their negative result.

it goes through three step:
- **learning**: accurate statistical analysis of the system behaviour
- **monitoring**: active statistical info collection of traffic, data, sequences, action
- **reaction**: comparison against statistical parameters

Active IDS always has someone who looks at IDS statistic



# topological features

## HIDS

## NIDS
