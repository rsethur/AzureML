## Train & Deploy a model using Azure ML Python SDK

#### Step 1: Clone the Azure ML Samples
1. Goto to new [ML workspace](https://ml.azure.com) (Called Studio now)
2. Navigate to `Notebooks` in the left nav
3. Expand the `Azure ML gallery` :arrow_right: `Samples` :arrow_right: `Python` :arrow_right: `1.x.x`
4. Hover over `How-to-use-azureml` :arrow_right: click on the three dots displayed in the right side :arrow_right: click `Clone`.

Now you will see the folder under your user files below.

#### Step 2: Create a notebook VM & launch it
1. Navigate to `Compute` in the left nav
2. Notebook VM Tab: Click `+New` -> choose a name and VM type (e.g. STANDARD_DS13_V2 which has 8 VCPUs)
3. Click Create
4. Once the Notebook VM is provisioned, you will see three links: `JupyterLab`, `Jupyter` and `R-Studio`. Open `Jupyter` and follow next steps.

#### Step 3: Train a model (Diabetes Dataset)
1. In `Jupyter`, open the notebook `train-on-amlcompute.ipynb`, in the folder `/howto-use-azureml/training/train-on-amlcompute`
<BR> It will prompt you to select a kernel: select `Python 3.6 AzureML` and click button `Set Kernel`. If you miss it accidentally, you can set it by going to top menu of the notebook: `Kernel` -> `Change kernel`
2. Run the notebook cell by cell
    * __Important__:
        1. When you are running the cells, it will ask you for interactive authentication: you need to follow the steps (follow the link and enter the supplied code).
        2. In the notebook no need to run from Section `Provision as a persistent compute target (Advanced)` onwards
3. After training is done, cleanup the compute cluster: In the last line uncomment this and execute `cpu_cluster.delete()`
4. __Explore your experiment run__: 
    1. In the new [Azure ML workspace](https://ml.azure.com/), navigate to the `Experiments` section in left nav
    2. Click on experiment name `train-on-amlcompute` -> `Run `
    3. Navigate to the `Metrics tab`. Check `alpha` and `mse` if not already checked
    4. Navigate to `Outputs` tab and you can see all the model files (pkl files) created by `train.py`.
    In the train.py you will see the model files are stored in ./outputs directory. Azure ML framework automatically moves all files in the outputs folder to the cloud workspace (including logs)
5. Take time to understand the code in the notebook and `train.py`

    ##### Optional (Hyper Param Tuning)
    Time permitting you can try this: In Jupyter landing page -> top nav `How to use Azure ML` -> `Ml Frameworks` -> `Scikit Learn` -> click clone on `train-hyperparameter-tune-deploy-with-sklearn`.
    This uses the diabetes dataset used by the next section (Deploy). 


#### Step 4: Deploy and score the model (Iris Dataset)
1. In `Jupyter`, open the notebook `model-register-and-deploy.ipynb`, in the folder `howto-use-azureml/deployment/deploy-to-cloud/`
2. Run the notebook cell by cell
<br>__Note__: Before running the last cell that deletes the deployed service, goto the new [ML workspace](ml.azure.com) and checkout `Endpoints` in the left nav
3. Take time to understand the code in the notebook and `score.py`

#### Optional Excercises
1. __Leverage AutoML__ via Azure ML Python SDK :Execute any automl notebook excercise from `MachineLearningNotebooks/how-to-use-azureml/automated-machine-learning`
2. __Leverage Databricks__ via Azure ML Python SDK : This is bit more involved as you need to execute this from Databricks workspace. Details are here: `MachineLearningNotebooks/how-to-use-azureml/automated-machine-learning/azure-databricks/README.md`
    
#### Clean up: 
Wait for the discussion to be over in the workshop before cleaning up.
<br>You can cleanup following instructions [here](https://docs.microsoft.com/en-us/azure/machine-learning/service/tutorial-first-experiment-automated-ml#clean-up-resources)