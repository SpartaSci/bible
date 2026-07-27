
# 2-PAM

- a pulse g(t) of amplitude A is used to represent 1
- a pulse g(t) of amplitude -A is used to represent 0


# M-ary PAM
- different M signal levels from $A_1 \to A_m$ in order to represent more information, not just 0 and 1
- Each signal level can be used to represent $log_2 M$ bits
- signals that are close can be mistaken, therefore, in order to minimize the risk of signal swapping, the **order** matters. [[signal analysis/grey coding|grey coding]]

example: m = 8 -> bits per levels = 3
![](https://people.eecs.ku.edu/~perrins/class/F08_700/lab/MPAM/8PAMConstellation.jpg)


## energy per bit
> a measure of the *energy efficiency* of the modulation can be obtain from the **average energy per bit**

$$E_b=\frac{E_{sign}}{log_2M}$$
Average energy per symbol divided by the number of bits carried by each symbol. The further it is from the origin 0, the higher is the energy  