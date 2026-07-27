
**Word2Vec** is an algorithm that extracts [[vecchio/AI 1/learned embedding|embedding]] for words starting from distributional hypotheses, since the semantics of a word depend on the context. The key intuitions of Word2Vec are:
1. predict the target word given the surrounding words;
2. predict the surrounding words given the central words;


## Skip-Gram model

The Skip-Gram model is an approach that falls under the second intuition of Word2Vec (i.e., predict surrounding words)

$$
\huge
\mathcal{L} = \sum_{t=1}^{T} \sum_{\substack{-c \leq j \leq c \\\\ j \neq 0}} \log P(w_{t+j} \mid w_t)
$$

- $\mathcal{L}$: funzione obiettivo da massimizzare
- $T$: numero totale di parole nel corpus
- $c$: dimensione della finestra di contesto
- $w_t$: parola centrale alla posizione $t$
- $w_{t+j}$: parola di contesto (entro la finestra, esclusa la centrale)
- $P(w_{t+j} \mid w_t)$: probabilità stimata che $w_{t+j}$ appaia nel contesto dato $w_t$


$$
\huge
P(w_{t+j} \mid w_t) = \frac{\exp\left( \mathbf{e}_{w_{t+j}}^\top \cdot \mathbf{e}_{w_t} \right)}{\sum_{w=1}^{V} \exp\left( \mathbf{e}_{w}^\top \cdot \mathbf{e}_{w_t} \right)}
$$

- $P(w_{t+j} \mid w_t)$: probabilità di osservare la parola $w_{t+j}$ nel contesto, dato $w_t$ (parola centrale)
- $\mathbf{e}_{w}$: vettore embedding (di uscita o di ingresso) della parola $w$
- $\mathbf{e}_{w_t}$: embedding della parola centrale
- $\mathbf{e}_{w_{t+j}}$: embedding della parola di contesto
- $V$: dimensione del vocabolario
- $\exp$: funzione esponenziale
- $\top$: trasposizione del vettore (dot product)

La formula è una **softmax**, che assegna probabilità più alte alle parole di contesto il cui embedding è **simile** (dot product alto) a quello della parola centrale.



