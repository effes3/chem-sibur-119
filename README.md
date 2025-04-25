# 🧪 Chemistry Meets ML: LogP Prediction for SIBUR "119 элемент" Challenge

### 🕵️‍♂️ Data Cleaning (a bit messy, but it worked)

The initial dataset contained ~12k molecules. We attempted to gather more data using augmentation (**check data_augmentation.ipynb for more info**) and simply adding more examples from datasets on **Kaggle**, **HuggingFace**, **GitHub** **platforms** and etc. but realized it was a bad idea because we were getting unsatisfactory results at the expense of time. So we tried a basic standardization on the primary dataset from "SIBUR" using **RDKit** and **Chython** libraries:

* Removed invalid SMILES  
* The duplicates were removed a little crookedly  
* Some molecules were processed incorrectly — for example, some valid examples were dropped  

In the end, we had a dataset with **10898** molecules: no duplicates, no invalid SMILES, everything is fine

Due to some misunderstandings we did not use the cleared dataset

For more information check **data_cleaning.ipynb**

### 💡 Finding the best way to predict LogP

Once we had finished data preprocessing, we started thinking about LogP prediction methods:

#### 1. Descriptors from RDKit and Mordred + Morgan Fingerprints + XGBRegressor + Optuna (check MolD_MolFP_pred.ipynb for more info), this part was prepared by [Grisha](https://t.me/LiAlHsBu3), also check **chem-sibur-119/grishapart**

* The best RMSE on public-leaderboard: **1.00064**
* The best RMSE on private-leaderboard: **1.00174**

Our gut feeling was that using molecular descriptors and molecular fingerprints would not allow us to achieve good RMSE because it's so easy to perform, so we did not spend much time on it. In short, using these parameters seemed very simple and inflexible to us, so we did not pay much attention to it. 

#### 2. Using GNN, in particular, DMPNN (check DMPNN_pred.ipynb for more info), this part was prepared by [Kirill](https://t.me/KiZeMin), also check **chem-sibur-119/kirillpart**

* The best RMSE on public-leaderboard: **0.930880**
* The best RMSE on private-leaderboard: **0.958848**

#### 3. Our final model using [Chemprop Library](https://github.com/chemprop/chemprop) (check Chemprop_pred.ipynb for more info), this part was mostly done by [Mikhail](https://t.me/sozhitelu), but we (Kirill and Grisha) also took some part in it, also check **chem-sibur-119/mishapart**

* The best RMSE on public-leaderboard: **0.672947**
* The best RMSE on private-leaderboard: **0.704836**

Due to some misunderstandings, we chose a bad solution to submit our application to the private-leaderboard, so we finished this hackathon in **15th place out of 42**, but we could have done better (taken a cleaned dataset and submitted the submission with the best RMSE on the public-leaderboard) and took **6-7th** place

### 🎓 Conclusions

#### 1. Data Quality Matters

* Despite initial efforts to augment the dataset, cleaner and more consistent data (like the final processed 10898 molecules) could have improved model performance. Future work should prioritize rigorous validation of preprocessing steps to avoid accidental exclusion of valid samples

#### 2. Model Selection & Flexibility

* Simple descriptor-based methods (RDKit/Mordred + XGBoost) underperformed (RMSE ~1.0), confirming their limitations for complex LogP prediction
* GNNs (DMPNN) showed better results (RMSE ~0.93–0.96), but the Chemprop-based model outperformed both (RMSE ~0.67–0.70), proving that task-specific architectures are critical

#### 3. Submission Strategy

* A misstep in leaderboard submission (using a suboptimal model version) cost us ~6–7 positions. Always validate the final pipeline before submission

#### 4. Key Takeaways

* Chemprop is a powerful tool for molecular property prediction, but requires careful hyperparameter tuning
* Team coordination is as important as technical work—clear communication could have prevented the dataset/leaderboard issues





