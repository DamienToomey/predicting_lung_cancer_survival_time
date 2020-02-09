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

- Highest validation C-index : ![](http://latex.codecogs.com/gif.latex?0.75)
- Predicted survival times on the test set are between ![](http://latex.codecogs.com/gif.latex?800) and ![](http://latex.codecogs.com/gif.latex?930) days.

### Second approach : Deep Learning 

- CNN for regression only on CT scans

[See jupyter-notebook on Google Colab (for GPU purposes)](https://colab.research.google.com/drive/1BImOfuIhQp6COx5Mg1gIBTJJs59XuhzV)

- Highest validation C-index : ![](http://latex.codecogs.com/gif.latex?0.72)
- Predicted survival times on the test set are between ![](http://latex.codecogs.com/gif.latex?0) and  ![](http://latex.codecogs.com/gif.latex?200) days.

### Remark on the 2 approaches

Eventhough the highest validation C-index for both approaches are quite close, the interval of the predicted survival times on the test set are very different.

It looks like the C-index is not a relevant metric.

My submission file is available [here](https://github.com/DamienToomey/predicting_lung_cancer_survival_time/blob/master/my_submission/submission.csv). The predictions were obtained with the first approach as the validation C-index is higher.

### Other approaches not explored here

- Try other metrics (mean squared error)
- Keep only data for people with Event equal to 1 (1=death observed) 
- Choose other variables in the data (clinical_data.csv, radiomics.csv) instead of the ones used for the baseline
- Regression on missing ages and histology and then take these variables into account when using autosklearn and lasso
- Dense Neural Network for regression on clinical_data.csv and radiomics.csv
- Use models available in [pycox](https://github.com/havakv/pycox)
    - `pip3 install pycox`
- CNN for regression on CT scans and fuse some variables from clinical_data.csv and radiomics.csv at some point in the network