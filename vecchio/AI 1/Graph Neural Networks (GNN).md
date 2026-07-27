
# How to model a GNN
GNNs have multiple architectures, such as 
- Graph Convolutional Network (GCN)
- Graph Sample and Aggregation (GraphSAGE)
- Graph Attention Network (GAT).



Regardless, the main steps are:
1. define a message: it represents the embedding;
2. define how to aggregate: it represents how to aggregate messages (i.e., the main difference among different architectures);
3. define the structure: it represents the stacking of multiple layers of the GNN;
4. define a task: it represents what is being classified (e.g., nodes, edges, graphs); this approach can be generalized to unsupervised tasks


---

## **1️⃣ Graph Convolutional Network (GCN)**

💡 **Idea**:  
Ogni nodo aggiorna la sua rappresentazione usando **tutti i suoi vicini** (incluso se stesso) prendendo la media delle loro feature trasformate.

📜 **Formula** (semplificata):

$$\huge
h_v^{(l)} = \sigma\left( \frac{1}{|N(v)|} \sum_{u \in N(v)} W^{(l)} h_u^{(l-1)} \right)
$$


- **N(v)** = vicini di v + sé stesso (self-loop)
    
- Dividere per $|N(v)|$ = **normalizzazione**
    
- Uguale peso a tutti i vicini (nessuna distinzione tra “più” o “meno” importanti)
    
- **Pro:** semplice ed efficiente
    
- **Contro:** non adatta a grafi molto grandi → serve tutta la matrice di adiacenza
    

📌 **Metafora**: come se ogni studente in una classe facesse media delle opinioni di **tutti** i compagni (più sé stesso) prima di cambiare idea.

---

## **2️⃣ GraphSAGE**

💡 **Idea**:  
Come GCN, ma invece di usare **tutti** i vicini, ne **campiona** un numero fisso e li aggrega (mean, pooling, LSTM…).

📜 **Formula** (semplificata):

$$\huge
h_v^{(l)} = \sigma\left( W^{(l)} \cdot \text{CONCAT}\left( h_v^{(l-1)}, \text{AGG}\left( \{ h_u^{(l-1)}, \forall u \in N(v) \} \right) \right) \right)
$$

- **Campionamento** → costante il numero di vicini
    
- **AGG** può essere:
    
    - mean
        
    - max-pooling
        
    - LSTM aggregator
        
- Concatenazione tra **sé stesso** e la media dei vicini
    
- **Pro:** scalabile a grafi enormi
    
- **Contro:** possibile perdita di informazione se si campionano pochi vicini
    

📌 **Metafora**: invece di chiedere l’opinione a **tutta** la classe, chiedi solo a **3 amici scelti a caso**, poi combini la loro media con la tua opinione.

---

## **3️⃣ Graph Attention Network (GAT)**

💡 **Idea**:  
Simile a GCN, ma **non** pesa tutti i vicini allo stesso modo → calcola **attenzioni** $\alpha_{vu}$ per dare più peso ai vicini più rilevanti.

📜 **Formula** (semplificata):

$$\huge
h_v^{(l)} = \sigma\left( \sum_{u \in N(v)} \alpha_{vu} \, W^{(l)} h_u^{(l-1)} \right)
$$

- αvu\alpha_{vu} = quanto nodo v “ascolta” nodo u  
    (imparato durante il training)
    
- Multi-head attention per stabilità
    
- **Pro:** può concentrarsi su vicini importanti
    
- **Contro:** più pesante computazionalmente
    

📌 **Metafora**: chiedi a **tutta** la classe, ma **dai più peso** all’opinione di chi reputi più competente.

---

### 📊 **Confronto rapido**

|Modello|Vicini usati|Peso vicini|Scalabilità|
|---|---|---|---|
|**GCN**|Tutti|Uguale|Medio|
|**GraphSAGE**|Campionati|Uguale|Alta|
|**GAT**|Tutti|Diverso (learned)|Medio-Bassa|


---

### **Task types**

1. **Node classification** → classificare i nodi usando i loro embedding  
    _Esempio_: rilevamento di comportamenti sospetti
    
2. **Link prediction** → prevedere archi mancanti o futuri  
    _Esempio_: probabilità di connessione tra nodi
    
3. **Graph classification** → classificare interi grafi in base a struttura e attributi  
    _Esempio_: rilevare comportamenti anomali da proprietà strutturali
    

---

### **Data split settings**

1. **Transductive setting**
    
    - Dataset = **un solo grafo**
        
    - Train, validation e test **sullo stesso grafo**
        
    - Il grafo è visibile in tutte le fasi
        
    - ❌ Non applicabile al _graph classification_
        
2. **Inductive setting**
    
    - Dataset = **più grafi**
        
    - Train, validation e test **su grafi diversi**
        
    - Ogni split vede solo parte del grafo/dataset
        
    - ✅ Applicabile al _graph classification_
        

---

### **Challenges in GNNs**

1. **Over-smoothing** → troppi layer → feature diventano indistinguibili
    
2. **Scalability** → grafi grandi = alto costo computazionale
    
3. **Heterogeneous graphs** → nodi/archi di tipo diverso richiedono architetture speciali
    
4. **Dynamic graphs** → struttura del grafo cambia nel tempo
    

---

