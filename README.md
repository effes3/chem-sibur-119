# 🧪 Chemistry Meets ML: LogP Prediction for SIBUR "119 элемент" Challenge

### 🕵️‍♂️ Data Cleaning (a bit messy, but it worked)

The initial dataset contained ~12k molecules. We attempted to gather more data using augmentation (**check data_augmentation.ipynb**) and simply adding more examples from datasets on **Kaggle**, **HuggingFace**, **GitHub** **platforms** and etc. but realized it was a bad idea because we were getting unsatisfactory results at the expense of time. So we tried a basic standardization on the primary dataset from "SIBUR" using **RDKit** and **Chython** libraries:

* Removed invalid SMILES  
* The duplicates were removed a little crookedly  
* Some molecules were processed incorrectly — for example, some valid examples were dropped  

In the end, we had a dataset with **10898** molecules: no duplicates, no invalid SMILES, everything is fine

Due to some misunderstandings we did not use the cleared dataset

For more information **check data_cleaning.ipynb**

### 💡 Finding the best way to predict LogP

Once we had finished data preprocessing, we started thinking about LogP prediction methods:

#### 1. Descriptors from RDKit and Mordred + Morgan Fingerprints + XGBRegressor + Optuna (check MolD_MolFP.ipynb for more info), this part was prepared by [Grisha](t.me/LiAlHsBu3)

The best RMSE on public-leaderboard: **1.00064**
The best RMSE on private-leaderboard: **1.00174**

Our gut feeling was that using molecular descriptors and molecular fingerprints would not allow us to achieve good RMSE, so we did not spend much time on it. In short, using these parameters seemed very simple and inflexible to us, so we did not pay much attention to it.

#### 2. Using GNN, in particular, DMPNN

The best RMSE on public-leaderboard: KirushaMiholap, dopolni pzh
The best RMSE on private-leaderboard: KirushaMiholap, dopolni pzh

#### 3. Our final model using [Chemprop Library](https://github.com/chemprop/chemprop) (check Chemprop_pred.ipynb for more info)

The best RMSE on public-leaderboard: **0.672947**
The best RMSE on private-leaderboard: **0.704836**

Due to some misunderstandings, we chose not the best solution for sending our submission to the private-leaderboard
