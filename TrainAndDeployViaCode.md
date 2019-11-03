## Train & Deploy a model using Azure ML Python SDK

#### Step 1: Create a notebook VM & launch it
1. Goto to new [ML workspace](ml.azure.com)
2. Navigate to `Compute` in the left nav
3. Notebook VM Tab: Click `+New` -> choose a name and VM type (e.g. STANDARD_DS13_V2 which has 8 VCPUs)
4. Click Create
5. Once the Notebook VM is provisioned, you will see three links: `JupyterLab`, `Jupyter` and `R-Studio`
6. For purposes of this workshop, select `Jupyter` (this leads to the Jupyter landing page) 

#### Step 2: Train a model (Diabetes Dataset)
1. In the `Jupyter` landing page, go to the tab `Azure ML Samples`
    1. `How to use Azure ML`  -> `Training` -> click `Clone` on `train-on-amlcompute`
    2. If notebook is not already opened:
        1. Navigiate to `Files` from the top nav -> goto folder `train-on-amlcompute`
        2. If notebook is not already opened: Open the notebook by clicking on it `train-on-amlcompute.ipynb`
2. Run the notebook cell by cell
    * __Important__: In the notebook no need to run from Section `Provision as a persistent compute target (Advanced)` onwards
3. After training is done, cleanup the compute cluster: In the last line uncomment this and execute `cpu_cluster.delete()`
4. __Explore your experiment run__: 
    1. In the new [Azure ML workspace](https://ml.azure.com/), navigate to the `Experiments` section in left nav
    2. Click on experiment name `train-on-amlcompute` -> `Run `
    3. Navigate to the `Metrics tab`. Check `alpha` and `mse` if not already checked
    4. Navigate to `Outputs` tab and you can see all the model files (pkl files) created by `train.py`.
    In the train.py you will see the model files are stored in ./outputs directory. Azure ML framework automatically moves all files in the outputs folder to the cloud workspace (including logs)
5. Take time to understand the code in the notebook and `train.py`

    ##### Optional (Hyper Param Tuning)
    Time permitting you can try this: In Jupyter landing page -> top nav `Azure ML Samples` -> `How to use Azure ML` -> `Ml Frameworks` -> `Scikit Learn` -> click clone on `train-hyperparameter-tune-deploy-with-sklearn`.
    This uses the diabetes dataset used by the next section (Deploy). 


#### Step 3: Deploy and score the model (Iris Dataset)
1. Similar to above, in the `Jupyter` landing page, go to the tab `Azure ML Samples`
    * `How to use Azure ML`  -> `Deployment` -> click `Clone` on `model-register-and-deploy`
2. Run the notebook cell by cell
<br>__Note__: Before running the last cell that deletes the deployed service, goto the new [ML workspace](ml.azure.com) and checkout `Endpoints` in the left nav
3. Take time to understand the code in the notebook and `score.py`

#### Optional Excercises
1. __Leverage AutoML__ via Azure ML Python SDK : Clone and execute any automl notebook excercise from the `Azure ML Samples` in jupyter landing page
2. __Leverage Databricks__ via Azure ML Python SDK : This is bit more involved as you need to execute this from Databricks workspace. Instructions [here](https://github.com/Azure/MachineLearningNotebooks/tree/master/how-to-use-azureml/azure-databricks).
    
#### Clean up: 
Wait for the discussion to be over in the workshop before cleaning up.
<br>You can cleanup following instructions [here](https://docs.microsoft.com/en-us/azure/machine-learning/service/tutorial-first-experiment-automated-ml#clean-up-resources)