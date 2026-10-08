# SO2 Surrogate Digital Twin

This project is a machine learning based surrogate model for an SO2 catalytic converter system. The main idea is to use a trained ML model to predict the behaviour of the process without having to run the complete simulation every time.

The project uses process data generated from simulation and a Random Forest Regression model to learn the relationship between the process inputs and the output variables.

## About the Project

Simulating a chemical process in detail can take a reasonable amount of time, especially when many different operating conditions need to be tested.

A surrogate model provides a faster way of getting predictions. Instead of running the full simulation for every case, the trained model can be used to estimate the required outputs from the given process conditions.

The overall workflow used in this project is:

```text
Process Simulation
       |
       v
Generate Dataset
       |
       v
Data Preparation
       |
       v
Train ML Model
       |
       v
Random Forest Surrogate
       |
       v
SO2 Prediction
```

The trained model can then be used as one part of a digital twin system.

## Project Objectives

* Generate process data for the SO2 system.
* Prepare the simulation data for machine learning.
* Train a regression based surrogate model.
* Predict the required SO2-related outputs.
* Reduce the time required for repeated predictions.
* Create a starting point for integrating the model into a digital twin.

## Project Structure

```text
so2-converter-digital-twin/
│
├── data/
│   └── sulfuric_acid_dataset.csv
│
├── dwsim/
│   └── s03_production.dwxmz
│
├── models/
│   ├── sulfuric_acid_rfr_surrogate.pkl
│   ├── target_columns.pkl
│   └── README.md
│
├── notebooks/
│   └── s02_surrogate_digital_twin.ipynb
│
├── .gitignore
└── README.md
```

The trained `.pkl` files are not included in the GitHub repository because the main surrogate model is approximately 2.15 GB. The model files are kept locally and can be regenerated using the training workflow.

## Tools and Technologies

The project was developed using:

* Python
* Jupyter Notebook
* Pandas
* NumPy
* Scikit-learn
* Random Forest Regression
* DWSIM
* Git and GitHub

## Machine Learning Model

A Random Forest Regression model is used as the surrogate model.

Random Forest was selected because it works well for nonlinear relationships and does not require the relationship between the process variables and the outputs to be known beforehand.

The basic process is:

1. Load the simulation dataset.
2. Separate input and target variables.
3. Prepare the data for training.
4. Train the Random Forest model.
5. Evaluate the predictions.
6. Save the trained model.
7. Use the saved model for future predictions.

## Dataset

The dataset used for training is stored in:

```text
data/sulfuric_acid_dataset.csv
```

The data is based on process simulation results and contains the variables required to train the surrogate model.

The dataset is used to establish the relationship between the operating conditions and the corresponding process outputs.

## DWSIM

DWSIM is used as part of the process simulation side of the project.

The simulation file is located at:

```text
dwsim/s03_production.dwxmz
```

The simulation provides the process data that is later used for developing the machine learning surrogate.

## Jupyter Notebook

The main development and training workflow is available in:

```text
notebooks/s02_surrogate_digital_twin.ipynb
```

The notebook contains the data preparation, model training and prediction workflow.

To open the notebook:

```bash
jupyter notebook
```

Then open:

```text
notebooks/s02_surrogate_digital_twin.ipynb
```

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/Eshwar8143/so2-converter-digital-twin.git
```

Move into the project directory:

```bash
cd so2-converter-digital-twin
```

### 2. Create a virtual environment

On Windows:

```powershell
python -m venv venv
```

Activate it:

```powershell
.\venv\Scripts\Activate.ps1
```

### 3. Install the required packages

```bash
pip install numpy pandas scikit-learn jupyter
```

If a `requirements.txt` file is added later, the dependencies can instead be installed using:

```bash
pip install -r requirements.txt
```

## Running the Project

After installing the dependencies, start Jupyter:

```bash
jupyter notebook
```

Open:

```text
notebooks/s02_surrogate_digital_twin.ipynb
```

The notebook can then be used to load the dataset, train the surrogate model and generate predictions.

## Digital Twin Approach

The idea behind the digital twin part of the project is to have a computational model that represents the behaviour of the actual process.

In this project, the machine learning surrogate acts as a faster representation of the process model.

```text
        Process / Plant
              |
              | Process Data
              v
        Data / Simulation
              |
              v
       ML Surrogate Model
              |
              v
       Predicted Outputs
              |
              v
        Digital Twin
```

With further development, the model could be connected to live process or sensor data so that predictions can be updated as the operating conditions change.

## Model Files

The trained models are intentionally excluded from GitHub.

The main model:

```text
models/sulfuric_acid_rfr_surrogate.pkl
```

is approximately 2.15 GB in size, which is too large for normal GitHub repository storage.

The `.pkl` files are therefore included in `.gitignore`.

The models can be regenerated by running the training process in the Jupyter notebook.

## Current Status

The current version of the project includes:

* Process simulation data
* DWSIM simulation file
* Data preparation workflow
* Random Forest surrogate model
* Model training workflow
* SO2 prediction workflow
* Initial digital twin structure

The project is still being developed and there are several areas that can be improved.


## Author

**Eshwar**

GitHub:
https://github.com/Eshwar8143

## License

This project does not currently include a separate license.
