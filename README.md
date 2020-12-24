# Databricks-MLflow-MLOps-AzureML

## Introduction
Using databricks mlflow model registry with azureml to build out an mlops pipeline

***MLflow Model Registry Web-hook for MLOps***

MLflow Model Registry is a central repository to store and query models for production use and  consumable across different teams. Users can publish and version models, discover new models and model  versions, request and approve stage transitions, pull information about models from production  systems, and download model artifacts.

Through the web-hook APIs you can automate devops pipelines

## Getting Started


## Dependencies

## Instructions



#### Create test web-hook 

```
json='{"model_name": "$model_name",    "events": ["TRANSITION_REQUEST_CREATED"],    "description": "Teams notifications",   "status": "TEST_MODE",    "http_url_spec": {      "url": "$webhook_url",      "secret": "anyRandomString"}}'
url='https://$region.azuredatabricks.net/api/2.0/mlflow/registry-webhooks/create'


result=`curl -X POST -H "Accept: application/json" -H "Authorization: Bearer ${token}" --data "$json" $url`
echo result: $result
```


#### List web-hook 

```
json='{"model_name": "$model_name"}'
url='https://$region.azuredatabricks.net/api/2.0/mlflow/registry-webhooks/list'
result=`curl -X GET -H "Accept: application/json" -H "Authorization: Bearer ${token}" --data "$json" $url`

echo result: $result
```

#### Test web-hook 

```
json='{"id":"$id"}'
url='https://$region.azuredatabricks.net/api/2.0/mlflow/registry-webhooks/test'
result=`curl -X POST -H "Accept: application/json" -H "Authorization: Bearer ${token}" --data "$json" $url`

echo result: $result
```

#### Activate the web-hook now
```

json='{"id":"$id", "status": "ACTIVE"}'
url='https://$region.azuredatabricks.net/api/2.0/mlflow/registry-webhooks/update'
result=`curl -X PATCH -H "Accept: application/json" -H "Authorization: Bearer ${token}" --data "$json" $url`

echo result: $result
```




## Output




