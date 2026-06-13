# CNC Tool Wear Detection using Machine Learning

## Overview

This project predicts the condition of CNC milling tools using machine learning techniques. The model utilizes machining experiment data and sensor measurements collected from CNC machines to estimate:

- Feedrate
- Clamp Pressure
- Tool Condition (Worn or Unworn)

The project demonstrates a complete machine learning workflow including data preprocessing, exploratory data analysis, feature selection, model training, and prediction.

---

## Dataset

The project uses the **Tool Wear Detection in CNC Mill** dataset.

### Files Used

- `train.csv`
- `experiment_01.csv` to `experiment_18.csv`

### Dataset Description

The dataset contains:

- Experiment metadata
- Tool condition labels
- Material information
- Feedrate settings
- Clamp pressure settings
- Sensor measurements from CNC machines, including:

  - Position values
  - Velocity measurements
  - Current feedback
  - Voltage readings
  - Output power
  - Machining process information

---

## Project Workflow

### 1. Import Required Libraries

The project uses:

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

Models explored include:

- Multi-Layer Perceptron (MLP)
- Decision Tree Classifier

---

### 2. Data Preprocessing

The training data is loaded from `train.csv`.

Categorical variables are encoded using `LabelEncoder`:

- Material
- Tool Condition
- Machining Finalized
- Feedrate
- Clamp Pressure

Unused columns are removed to simplify the dataset.

---

### 3. Exploratory Data Analysis

Correlation heatmaps are generated to understand relationships between variables.

Heatmaps are created for:

- Training metadata
- Combined experiment sensor data
- Reduced feature datasets

These visualizations help identify the most informative features.

---

### 4. Experiment Data Integration

Sensor data from all 18 experiments are loaded and merged.

For each experiment:

- Machining process labels are encoded.
- Corresponding feedrate labels are attached.
- Corresponding clamp pressure labels are attached.

All experiment datasets are concatenated into a single dataframe.

---

### 5. Feature Selection

Correlation analysis is used to identify important features.

#### Feedrate Prediction Features

Selected based on correlation with encoded feedrate.

Examples include:

- X/Y/Z positions
- Command positions
- Spindle velocity
- Current feedback
- DC bus voltage
- Output voltage
- Output power
- Feedrate measurements

---

#### Clamp Pressure Prediction Features

Selected based on correlation with encoded clamp pressure.

Examples include:

- Position measurements
- Output currents
- Velocity measurements
- Output voltage
- Feedrate measurements

---

### 6. Feedrate Prediction

The feedrate prediction problem is formulated as a classification task.

Models trained:

#### Multi-Layer Perceptron

```python
MLPClassifier(
    solver='lbfgs',
    alpha=1e-5,
    hidden_layer_sizes=(5, 2),
    random_state=1
)
