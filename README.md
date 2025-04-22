# 🧪 Chemistry Meets ML: LogP Prediction for SIBUR "119 элемент" Challenge

### 🕵️‍♂️ Data Cleaning (a bit messy, but it worked)

The initial dataset contained ~40k molecules from various sources. We attempted a basic standardization using RDKit:

* Removed invalid SMILES  
* Messy dropped duplicates (based on SMILES)  
* Some molecules were processed incorrectly — for example, some valid were dropped
