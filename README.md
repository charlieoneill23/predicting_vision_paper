# Vision is all you need: using minimal data and machine learning to predict patient vision without imaging biomarkers
Predicting nAMD patient vision using machine learning. Our top-performing model, TabNet, achieved results almost twice as good as published regression baselines using a 10th of the input features, and without using any imaging biomarkers.

## Repository structure
The repository follows a standard structure:
* [input](https://github.com/charlieoneill11/predicting_vision_paper/tree/main/input) contains both the patient data as well as the notebook used to preprocess, clean and feature engineer the data. The three main datasets for prediction of OVC at the end of the first, second and third year respectively are `df_1_years.csv`, `df_2_years.csv` and `df_3_years.csv`. Neither train-valid splits nor k-fold cross validation splits have been provided, but rather are undertaken in the training scripts themselves.
* [models](https://github.com/charlieoneill11/predicting_vision_paper/tree/main/models) contains notebooks used for experimenting and producing results. The notebooks are divided into the classification and regression tasks.
* [training](https://github.com/charlieoneill11/predicting_vision_paper/tree/main/training) contains the Python scripts allowing the user to train and evaluate different models on the required dataset from the command line. The main script is [`train_classify.py`](https://github.com/charlieoneill11/predicting_vision_paper/blob/main/training/train_classify.py) and [`train_regression.py`](https://github.com/charlieoneill11/predicting_vision_paper/blob/main/training/train_regression.py), both of which rely on the other scripts for configuration, dataset retrieval and argument parsing.
* [results](https://github.com/charlieoneill11/predicting_vision_paper/tree/main/results) contains figures and outputs from the model training and evaluation runs. I plan to update this to include JSON outputs of final hyperparameters and Pytorch model weights.

## Training and evaluating models
Navigate into the [training](https://github.com/charlieoneill11/predicting_vision_paper/tree/main/training) folder and open a terminal. Change the [`config.py`](https://github.com/charlieoneill11/predicting_vision_paper/blob/main/training/config.py) file to the appropriate paths. Run `python train.py --model --year`, where `model` and `year` are arguments passed in at the command line representing the model used for prediction and the end year OVC is being predicted at. You can alter the hyperparameters of the available models, or even add models yourself, in the [`model_dispatcher.py`](https://github.com/charlieoneill11/predicting_vision_paper/blob/main/training/model_dispatcher.py) file.

To train a vanilla neural network, run
```bash
python vanilla_nn.py --years 3
```
