# 🧪 Chemistry Meets ML: LogP Prediction for SIBUR "119 элемент" Challenge

### 🕵️‍♂️ Data Cleaning (a bit messy, but it worked)

The initial dataset contained ~12k molecules. We attempted to gather more data from **Kaggle**, **HuggingFace**, **GitHub** and etc. but realized it was a bad idea because we were getting unsatisfactory results at the expense of time. So we tried a basic standardization on the primary dataset from "SIBUR" using **RDKit** and **Chython** libraries:

* Removed invalid SMILES  
* The duplicates were removed a little crookedly  
* Some molecules were processed incorrectly — for example, some valid examples were dropped  

In the end, we had a dataset with 10898 molecules: no duplicates, no invalid SMILES, everything is fine

Due to some misunderstandings we did not use the cleared dataset

For more information check data_cleaning.ipynb 

### 💡 Finding the best way to predict LogP

When we finished our data preprocessing 

