# QMOF Bandgap Prediction

## Project
The goal of this project is to predict the **bandgap** of a MOF from the structural, geometric, symmetry, chemical, and energetic characteristics.

## Dataset
The data came from the **QMOF** database. 
`qmof.csv` is the file that contains all the information we are going to use:
- **Structural and geometric features**: `info.natoms`, `info.density`, `info.volume`, `info.pld`, `info.lcd`
- **Symmetry features**: `info.symmetry.spacegroup`, `info.symmetry.pointgroup`
- **Energy features**: `outputs.pbe.energy_vdw`, `energy_per_atom`, etc.
- **Target**: `outputs.pbe.bandgap`

## Data Preprocessing Pipeline
Before the training of the model, we process the data through the following steps:
1. **Feature Engineering**: Calculation of new physically relevant variables, such as energy per atom (`energy_per_atom`).
2. **Handling Missing Values**: Removal of records containing `NaN` (null values) in both the predictive features and the target variable (`outputs.pbe.bandgap`).
3. **One-Hot Encoding**: Conversion of textual symmetry variables (e.g., point groups and space groups) into numerical vector formats using `pd.get_dummies()` to make them compatible with machine learning algorithms.

## Dependencies
To run the code, we need:
- `pandas`
- `numpy`
- `scikit-learn` *(Aggiungere se si usano modelli ML)*
- `matplotlib` / `seaborn` *(Aggiungere se si fanno grafici)*

## Bibliography
- A.S. Rosen, S.M. Iyer, D. Ray, Z. Yao, A. Aspuru-Guzik, L. Gagliardi, J.M. Notestein, R.Q. Snurr. "Machine Learning the Quantum-Chemical Properties of Metal–Organic Frameworks for Accelerated Materials Discovery", *Matter*, 4, 1578-1597 (2021).
- A.S. Rosen, V. Fung, P. Huck, C.T. O'Donnell, M.K. Horton, D.G. Truhlar, K.A. Persson, J.M. Notestein, R.Q. Snurr. "High-Throughput Predictions of Metal–Organic Framework Electronic Properties: Theoretical Challenges, Graph Neural Networks, and Data Exploration", *npj Comput. Mater.*, 8, 195 (2022).
