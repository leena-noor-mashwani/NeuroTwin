# NeuroTwin 🧠

### A Machine Learning Digital Twin of a Hodgkin-Huxley Neuron

## Introduction

Neurons are specialized cells in the nervous system that communicate by producing electrical signals. When a neuron receives enough stimulation, it can generate an electrical impulse called an **action potential**, commonly described as the neuron "firing."

Understanding when and how a neuron fires is important in computational neuroscience. One well-known mathematical model used to study this behavior is the **Hodgkin-Huxley model**.

The Hodgkin-Huxley model describes how changes in ion conductances and electrical current influence the membrane potential of a neuron. Although it provides a powerful way to simulate neuronal behavior, repeatedly running a detailed mathematical simulation can be computationally expensive.

**NeuroTwin** explores how machine learning can be used as a computational surrogate for this process.

Instead of running the full Hodgkin-Huxley simulation every time, NeuroTwin learns patterns from simulated neuronal behavior and predicts whether a neuron will fire based on its input parameters. The machine learning prediction can then be compared with the original Hodgkin-Huxley simulation.

## What is a Digital Twin?

A **digital twin** is a computational representation of a real-world system that can be used to study or predict the behavior of that system.

In this project, the Hodgkin-Huxley neuron acts as the reference system, while the machine learning model acts as its predictive digital representation.

```text
Hodgkin-Huxley Neuron
        ↓
Generate Simulation Data
        ↓
Train Machine Learning Model
        ↓
NeuroTwin
        ↓
Predict Neuronal Firing
```

## What is the Hodgkin-Huxley Model?

The Hodgkin-Huxley model is a mathematical model of neuronal electrical activity. It describes how the movement of ions such as sodium and potassium affects the electrical potential across a neuron's membrane.

The model uses parameters representing different ion conductances and an applied electrical current to simulate whether the neuron produces an action potential.

For this project, the main parameters are:

* **Input Current** — electrical stimulation applied to the neuron.
* **g_Na** — sodium conductance.
* **g_K** — potassium conductance.
* **g_L** — leak conductance.

The Hodgkin-Huxley simulation provides the reference behavior used to train and validate NeuroTwin.

## How NeuroTwin Works

NeuroTwin follows a machine learning workflow:

1. Neuronal parameters are provided to the Hodgkin-Huxley simulation.
2. The simulation produces neuronal behavior.
3. The simulation results are used to create a machine learning dataset.
4. Machine learning models learn the relationship between the parameters and neuronal firing.
5. NeuroTwin predicts whether a neuron will fire.
6. The prediction is compared with the original Hodgkin-Huxley simulation.

## Machine Learning Models

Two classification models were evaluated:

* **Logistic Regression**
* **Random Forest**

The models were trained to classify neuronal behavior into two states:

* **FIRED**
* **DID NOT FIRE**

The Random Forest model was selected for the NeuroTwin prediction system.

## NeuroTwin Inputs

The model uses four main input features:

| Feature         | Meaning                                  |
| --------------- | ---------------------------------------- |
| `input_current` | Electrical current applied to the neuron |
| `g_Na`          | Sodium conductance                       |
| `g_K`           | Potassium conductance                    |
| `g_L`           | Leak conductance                         |

The model produces a prediction together with the estimated probability of firing.

## Validation

To evaluate how well NeuroTwin reproduces the behavior of the Hodgkin-Huxley simulation, it was tested on **50 independently generated validation cases**.

Results:

* **Correct predictions:** 46 / 50
* **Agreement with Hodgkin-Huxley:** 92%
* **False positives:** 2
* **False negatives:** 2

At the 0.50 decision threshold:

* **Accuracy:** 92%
* **Precision:** 94.44%
* **Recall:** 94.44%

These results represent the performance observed on the 50 validation cases and should not be interpreted as universal accuracy for all possible neuron parameters.

## Confusion Matrix

The independent validation produced:

```text
                 NeuroTwin
              No Fire   Fired

HH No Fire       12       2
HH Fired          2      34
```

This means NeuroTwin correctly identified 12 non-firing cases and 34 firing cases, while producing 2 false positives and 2 false negatives.

## Interactive NeuroTwin

The project also includes an interactive interface where users can change:

* Input Current
* Sodium Conductance
* Potassium Conductance
* Leak Conductance

The system then displays:

* NeuroTwin prediction
* Probability of firing
* Hodgkin-Huxley result
* Spike count
* Firing rate
* Agreement between the machine learning model and the simulation

The project also visualizes the neuron's membrane potential over time, allowing users to observe the electrical activity produced by the Hodgkin-Huxley simulation.

### Project Visualizations

#### Hodgkin-Huxley Neuron Activity
![Neuron Waveform](neuron_waveform.png)

#### NeuroTwin Validation
![Confusion Matrix](confusion_matrix.png)

#### Interactive NeuroTwin Dashboard
![NeuroTwin Dashboard](neurotwin_dashboard.png)

## Project Workflow

```text
Neuron Parameters
       ↓
Hodgkin-Huxley Simulation
       ↓
Simulation Dataset
       ↓
Data Preparation
       ↓
Machine Learning Models
       ↓
Model Evaluation
       ↓
Random Forest NeuroTwin
       ↓
Firing Prediction
       ↓
Comparison with Hodgkin-Huxley
       ↓
Neuron Activity Visualization
```

## Main Features

* Hodgkin-Huxley neuron simulation
* Machine learning-based neuronal firing prediction
* Logistic Regression evaluation
* Random Forest classification
* Firing probability estimation
* Independent validation against Hodgkin-Huxley
* Confusion matrix analysis
* Decision threshold analysis
* Interactive neuron parameters
* Membrane-potential visualization
* Saved trained machine learning model

## Technologies

* Python
* NumPy
* Pandas
* Matplotlib
* Scikit-learn
* Joblib
* IPyWidgets
* Google Colab
* GitHub

## Project Files

| File                     | Description                                                                                                            |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| `NeuroTwin.ipynb`        | Complete project notebook containing the simulation, data preparation, machine learning, validation, and visualization |
| `neurotwin_model.pkl`    | Trained Random Forest model                                                                                            |
| `neurotwin_features.pkl` | Saved feature information used by the model                                                                            |
| `requirements.txt`       | Python libraries required for the project                                                                              |

## Future Development

Possible future extensions include:

* Larger and more diverse Hodgkin-Huxley simulation datasets
* More detailed neuronal state prediction
* Deep learning-based surrogate models
* Real-time neuronal simulation
* Web-based NeuroTwin interface
* Visualization of additional Hodgkin-Huxley variables
* Extension to other computational neuron models

## Author

**Leena Noor Mashwani**

BS Software Engineering | Machine Learning & AI
