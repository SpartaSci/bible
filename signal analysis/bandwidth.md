
> is the interval of frequencies occupied by a signal




most popular definition are related to $\lvert X(f)^2\rvert$ like the 3dB Bandwidth


> [!attention] why 3db
> Because finite duration signals have infinite support in the frequency domain.


**baseband signals**: signals whose frequency spectrum is concentrated around zero

**bandpass signals**: signals whose frequency spectrum centred at some frequency $f_c$ away from zero

[[signal analysis/_signal|_signal]]

# bandwidth occupancy
>by acting on the basis pulse we can change the signal bandwidth when represented in the frequency domain.


# bandwidth efficiency
We want to choose the pulse shape g(t) in order to put more energy in a small bandwidth.

For a pulse of duration T, we can define:
- symbol rate: $R_s=\frac{1}{T}$
- there are $log_2M$ bits per symbol
- bit rate: $R_b = log_2M * R_s$
- two-sided bandwidth is $BW=2*R_s=\frac{2}{T}$
- **Bandwidth efficiency**:$$\frac{R_b}{BW}=\eta=\frac{log_2M}{2} \ bps/Hz$$
A bandwidth efficiency possesses the following properties:
- as M (bits per symbol) increases, BW increases, however as M increases we are more prone to errors as symbol are close together
- as T increase it narrows down the bandwidth
- *Solution*: trade-off between distance from different symbol and energy needed to generate more far-away signals 

## bandwidth efficiency vs energy efficiency
- BE efficiency increases with increasing M (bits per symbol)
- for a fixed energy level as M increases we are more prone to errors, since it results in *closer* symbols
- need to **increase** symbol energy level to overcome errors
- but by increasing the symbol energy level, i can increase M with no problems regarding errors, but the energy efficiency will be lower
- Resulting in a **trade-off** between *Bandwidth efficiency* and *Energy efficiency*


>Increase *Bandwidth efficiency* -> increase M -> more errors -> increase energy to overcome -> decrease *Energy efficiency* -> but we care about it so -> increase *Energy efficiency* -> decrease *Bandwidth efficiency*

*Energy efficiency* <-> **Trade-off** <-> *Bandwidth efficiency* 

