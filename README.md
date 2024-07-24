<h2>Problem Introduction</h2>

In this notebook, we will set up and end-to-end process to preprocess, train, and deploy an XGBoost model to an endpoint in AWS SageMaker. The dataset we use is taken from WinJi (https://www.win-ji.com), which is an asset management platform for renewables. The dataset contains various physical measurements as per the column definition below:

| Column name        | Description                                                                           | Unit | Data Type |
|:-------------------|:--------------------------------------------------------------------------------------|:-----|:----------|
| wt_sk              | Unique device identifier, equivalent to device name                             | -    | float     |
| measured_at        | Data timestemp in UTC format                                                          | -    | string    |
| wind_speed         | Average apparent wind speed measured by nacelle anemometer, normalised to rated value | m/s  | float     |
| power              | Average measured power production, normalised to rated max power                      | W    | float     |
| nacelle_direction  | Average position of nacelle relative to North (E=90°)                                 | °    | float     |
| wind_direction     | Average direction of incoming wind relative to North (E=90°)                          | °    | float     |
| rotor_speed        | Average revolutions per minute of the low speed rotor, normalised to rates RS         | -    | float     |
| generator_speed    | Average revolutions per minute of the generator, normalised to rated GS               | -    | float     |
| temp_environment   | Average outside temperature on nacelle height                                         | °C   | float     |
| temp_hydraulic_oil | Average oil temperature                                                               | °C   | float     |
| temp_gear_bearing  | Average gear temperature                                                              | °C   | float     |
| cosphi             | Average power factor of device                                                        | -    | float     |
| blade_angle_avg    | Average pitching angles, averaged over blades                                         | °    | float     |
| hydraulic_pressure | Average pressure in hydraulic circuit                                                 | mBar | float     |
| subtraction        | Error flag (NaN: no error, 0/1: error)                                                | -    | float     |
| categories_sk      | Categorisation of error type                                                          | -    | float     |

Values have been obfuscated and white noise added to prevent leakage of proprietary information. For details on the exploration of the dataset, see the data exploration notebook (sagemaker_eda/EDA_SageMaker.ipynb).

The goal in this notebook is to use AWS SageMaker to predict an error state for a turbine (column `subtraction`) using an XGBoost model.

# How to use this repository

1. Start AWS SageMaker Studio
2. Clone the repository in SageMaker
3. Open and work through the exploratory data analysis notebook in
4. Open and work through the notebook about using AWS SageMaker to build an XGBoost model and deploy it to an endpoint

- The notebook is located in `/sagemaker_xgboost_notebook/`

6. Follow the details in the blogpost and use the content in `/sagemaker_pipeline/` to build an MLOps pipeline with AWS SageMaker
