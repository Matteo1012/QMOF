# QMOF Bandgap Prediction

## 📄 Descrizione del Progetto
Questo progetto si pone l'obiettivo di applicare tecniche di Machine Learning per prevedere il **bandgap** (la banda proibita) di materiali di tipo MOF (Metal-Organic Frameworks) partendo dalle loro caratteristiche strutturali, geometriche e di simmetria.

I dati provengono dal database **QMOF** (Quantum MOF Database).

## 📊 Il Dataset
Il file principale utilizzato per questo progetto è `qmof.csv`. Contiene numerose informazioni estratte tramite calcoli DFT (Density Functional Theory), tra cui:
- **Feature geometriche e strutturali**: `info.natoms`, `info.density`, `info.volume`, `info.pld`, `info.lcd`.
- **Feature di simmetria**: `info.symmetry.spacegroup`, `info.symmetry.pointgroup`.
- **Feature energetiche calcolate**: `outputs.pbe.energy_vdw`, energia per atomo, ecc.
- **Target**: `outputs.pbe.bandgap`.

## ⚙️ Pipeline di Pre-processing dei Dati
Prima dell'addestramento del modello, i dati grezzi vengono sottoposti a una fase di pulizia e feature engineering:
1. **Risoluzione DtypeWarnings**: Lettura sicura del dataset CSV includendo `low_memory=False` in Pandas.
2. **Feature Engineering**: Calcolo di nuove variabili fisicamente rilevanti, come l'energia per atomo (`energy_per_atom`).
3. **Gestione dei Valori Mancanti**: Rimozione dei record contenenti `NaN` (valori nulli) sia nelle feature predittive che nella variabile target (`outputs.pbe.bandgap`).
4. **One-Hot Encoding**: Conversione delle variabili di simmetria testuali (es. point group e space group) in formati vettoriali numerici tramite `pd.get_dummies()`, per renderli compatibili con gli algoritmi di machine learning.

## 🛠️ Requisiti (Dependencies)
Per eseguire il codice di questo progetto sono necessarie le seguenti librerie Python:
- `pandas`
- `numpy`
- `scikit-learn` [Aggiungere se si usano modelli ML]
- `matplotlib` / `seaborn` [Aggiungere se si fanno grafici]

Puoi installare i requisiti tramite pip:
```bash
pip install pandas numpy scikit-learn


A.S. Rosen, S.M. Iyer, D. Ray, Z. Yao, A. Aspuru-Guzik, L. Gagliardi, J.M. Notestein, R.Q. Snurr. "Machine Learning the Quantum-Chemical Properties of Metal–Organic Frameworks for Accelerated Materials Discovery", Matter, 4, 1578-1597 (2021).
A.S. Rosen, V. Fung, P. Huck, C.T. O'Donnell, M.K. Horton, D.G. Truhlar, K.A. Persson, J.M. Notestein, R.Q. Snurr. "High-Throughput Predictions of Metal–Organic Framework Electronic Properties: Theoretical Challenges, Graph Neural Networks, and Data Exploration," npj Comput. Mat., 8, 195 (2022).
