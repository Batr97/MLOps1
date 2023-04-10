# Batyrkhan_Gainitdinov
MADE 2022 

The ML project implements the classification of the dataset https://www.kaggle.com/datasets/cherngs/heart-disease-cleveland-uci . Two training models were used (Logistic Regression and KNeighborsClassifier), the choice of which is configured from the my_config#1 config file.yaml with the 'model' key.
The project structure was taken from cookiecutter-data-science https://drivendata.github.io/cookiecutter-data-science /, removed all unnecessary directories.
Regarding completed items:
- EDA is made both in the form of a laptop .ipynb, and in the form of a script that unloads .html reports to the reports directory.
- The functions for training and forecasting the model are written (designed as a command-line utility) on test data (the data is in the data/processed/train_df.csv & test_df.scv folder), training and forecasting is started from the folder src/models/train_model.py & predict_model.py, respectively. The call instructions are written in the readme
- The project has a modular structure
- And loggers are also implemented that write logs to the src/logs folder. 3 log files are implemented for working with data, for training and forecasting the model.
- There is.py file for testing in the src/tests folder, implemented with the help of Pytest, for training prediction and data preprocessing.
- Synthetic data is generated in src/data/synthetic_data_gen.py . The size of the dataset corresponds to the original data uploaded from Kaggle, size 247x13. But in it categorical signs are not OneHotEncoded. Therefore, when calling the forecast, errors may occur when training on different data (synthetic and original).
- 2 config files were created in the format .yaml, my_config#1.yaml and my_config#2.yaml, the second one is used for the KNeighborsClassifier model, which we set in my_config#1.yaml with the 'model' key = 'KNN'.
- A transformer has been written. It is located in the src/features folder. File feature_selector.py selects categorical and numerical features, which are then submitted to the pipeline pipeline.py . Categorical features pass through OneHotEncoding, and numeric ones pass through StandardScaler, then these data are combined into one dataframe and submitted to model training.
- Dataclasses are used for entities from the config, not bare dicts. Specifically in the ml_project/dataclass_config file.py has written a dataclass for the config my_config#1.yaml. An example of its use can be seen during the training of the model, that is, in the file src/models/train_model.py .
- The project has fixed all the dependencies in the file requirements.txt CI is configured for running tests, linter based on github actions