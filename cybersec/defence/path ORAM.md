---
tags:
  - memory
---
> Path ORAM is a simple oblivious RAM algorithm. While using cloud platform or any other insecure memory, attack can be made using the access pattern. Oblivious RAM is the way to hide the memory access pattern with some extra bandwidth and memory overhead.

> Path ORAM changes the location of block repeatedly and accesses the whole branch for a single block. Therefore, the pattern of access is always random. However, the security is dependent mostly on the random branch selection of the blocks. 


# protect against
[[snooping|snooping attack]] can target extracting data (protected with encryption) or extracting access patterns to learn what a program is doing