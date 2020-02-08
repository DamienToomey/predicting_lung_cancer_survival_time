## Predicting lung cancer survival time by OWKIN

Challenge website : https://challengedata.ens.fr/challenges/33

---

### Problem

- supervised survival prediction problem
- predict the survival time of a patient (remaining days to live) from one three-dimensional CT scan (grayscale image) and a set of pre-extracted quantitative imaging features, as well as clinical data

---

### First approach : Machine Learning
- autosklearn on clinical_data.csv and radiomics.csv
- Lasso on clinical_data.csv and radiomics.csv

[See jupyter-notebook on this repository](https://github.com/DamienToomey/predicting_lung_cancer_survival_time/blob/master/code/code.ipynb)

### Second approach : Deep Learning 

- CNN for regression only on CT scans

[See jupyter-notebook on Google Colab (for GPU purposes)](https://colab.research.google.com/drive/1BImOfuIhQp6COx5Mg1gIBTJJs59XuhzV)

### Other approaches not explored here

- Choose other variables in the data (clinical_data.csv, radiomics.csv) instead of the ones used for the baseline
- Regression on missing ages and histology and then take these variables into account when using autosklearn and lasso
- Dense Neural Network for regression on clinical_data.csv and radiomics.csv
- Use models available in [pycox](https://github.com/havakv/pycox)
    - `pip3 install pycox`
- CNN with CT scans and fuse some variables from clinical_data.csv and radiomics.csv at some point in the network