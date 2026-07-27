

Il **Bag of Words** è una tecnica semplice per rappresentare frasi o documenti come **vettori numerici**, contando **quante volte appaiono le parole** di un vocabolario.

---

### 📊 **Come funziona**

1. **Costruisci un vocabolario** con tutte le parole che appaiono nel tuo corpus (es. `["w1", "w2", "w3"]`).
    
2. Per ogni frase (o documento), **conti quante volte** ogni parola del vocabolario appare.
    
3. La frase diventa un **vettore di conteggi**, uno per parola.
    

Esempio:

|Frase (`si`)|w1|w2|w3|
|---|---|---|---|
|s1|1|1|1|
|s2|1|1|0|
|s3|0|1|2|
|s4|1|0|2|

---

### ⚠️ **Limiti**

- ❌ **Perde l'ordine** delle parole (“cane morde uomo” ≈ “uomo morde cane”)
    
- ❌ **Ignora il significato** e il contesto
    
- ❌ **Alta dimensionalità** se il vocabolario è grande (sparso e inefficiente)
    

---

### ✅ **Punti di forza**

- ✅ Semplice
    
- ✅ Facile da implementare (`CountVectorizer` di scikit-learn)
    
- ✅ Buon baseline per modelli semplici come Naive Bayes o SVM
    



```
from sklearn.feature_extraction.text import CountVectorizer

# Frasi di esempio
corpus = [
    "il gatto dorme",
    "il cane abbaia",
    "il gatto e il cane giocano",
    "il cane dorme molto"
]

# Inizializza il vettorizzatore
vectorizer = CountVectorizer()

# Applica il BoW al corpus
X = vectorizer.fit_transform(corpus)

# Stampa le parole nel vocabolario
print("Vocabolario:", vectorizer.get_feature_names_out())

# Stampa la matrice BoW (come array)
print("\nMatrice BoW (frasi x parole):")
print(X.toarray())

```