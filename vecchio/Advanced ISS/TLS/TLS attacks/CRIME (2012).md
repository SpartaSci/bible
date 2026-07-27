an attacker able to inject *chosen plaintext* in the user requests and measure the size of the encrypted traffic may recover specific plaintext parts by exploiting information leaked from the compression 


it is generally good to perform compression before encryption because it reduces similarities between data and, by doing so, it makes encryption more efficient. However, compression could leak information regarding data that’s been sent (e.g., cookies).

With an adaptive chosen plaintext attack, if the plaintext contains a word which is been used somewhere else during the data exchange, the compression algorithm will reduce the size of the message. If the message size has been reduced, it means some bits in the plainext have matched something;