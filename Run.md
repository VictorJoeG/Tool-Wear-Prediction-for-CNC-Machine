How to Run
Clone the Repository
git clone https://github.com/yourusername/cnc-tool-wear-detection.git
cd cnc-tool-wear-detection
Install Dependencies
pip install numpy pandas matplotlib seaborn scikit-learn
Dataset Structure

Place the dataset files as follows:

input/
└── tool-wear-detection-in-cnc-mill/
    ├── train.csv
    ├── experiment_01.csv
    ├── experiment_02.csv
    ├── ...
    └── experiment_18.csv
Run the Script
python main.py
Technologies Used
Python 3
NumPy
Pandas
Matplotlib
Seaborn
Scikit-learn
Limitations
Label encoding imposes ordinal relationships on categorical variables.
Feature selection relies solely on correlation thresholds.
Model evaluation uses a single train-test split.
Hyperparameter tuning was not performed.
Additional models and cross-validation may improve performance.
Future Improvements
Implement k-fold cross-validation.
Perform hyperparameter optimization using GridSearchCV.
Evaluate additional algorithms such as Random Forest and XGBoost.
Add classification reports and confusion matrices.
Develop a real-time monitoring dashboard for CNC tool wear prediction.
Note

This project is intended for educational and research purposes to demonstrate the application of machine learning techniques in predictive maintenance and smart manufacturing environments.


### Potential Issues in the Current Code

Before publishing this project, consider fixing these issues:

1. Missing import formatting:
   ```python
   from sklearn import treeimport pandas as pd

should be:

from sklearn import tree
import pandas as pd

SGD_tool_condition is used but never defined:

pred = SGD_tool_condition.predict(finalDf)

You may have intended to use:

pred = tree_tool_condition.predict(finalDf)
The feedrate and clamp pressure decoding logic using np.sign() is incorrect and will not recover the original labels.
The dataframe finalDf generated from predictions may not align with the size expected for tool condition prediction.

Addressing these issues will improve the reproducibility and correctness of the project.
