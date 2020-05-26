# SageMaker Deployment Project

The notebook and Python files provided here, once completed, result in a simple web app which interacts with a deployed recurrent neural network performing sentiment analysis on movie reviews.

## Files

### `train`

The `train`directory includes python scripts with the RNN model architecture in PyTorch and the training loop. The model architecture consists of an embedding layer of the input data, followed by a Long-Short Term Memory recurrent neural network, a linear layer and a sigmoid activation function that outputs the estimated sentiment of the movie review. The `train.py` script accepts input data already preprocessed, and performs the training loop according to the specified hyperparameters, including epochs, batch size, layer dimensions and vocabulary size, among others.

### `serve`

The `serve` directory includes the model and predict files that will be used to deploy the trained model to be used by the sentiment analysis web app. Additionally, it includes a `utils.py` file to preprocess any raw input text. The functions in this file will be used by the predict functions to create a full working pipeline to be deployed on the SageMaker endpoint. 

### `website`

The `website` directory include the html website file, to be updated with the newly created endpoint url.

### `sentiment_analysis.ipynb`

This Jupyter Notebook file contains the Sagemaker notebook integrating all files aforementioned to run the project. It contains a series of instructions to be followed and better understand the project.

## Setup

The notebook and auxiliary files provided in this repository are intended to be executed using Amazon's SageMaker platform. The following is a brief set of instructions on setting up a managed notebook instance using SageMaker, from which the notebook can be completed and run.

### Log in to the AWS console and create a notebook instance

Log in to the AWS console and go to the SageMaker dashboard. Click on `Create notebook instance`. The notebook name can be anything and using ml.t2.medium is a good idea as it is covered under the free tier. For the role, creating a new role works fine. Using the default options is also okay. Important to note that you need the notebook instance to have access to S3 resources, which it does by default. In particular, any S3 bucket or object with sagemaker in the name is available to the notebook.

### Use git to clone the repository into the notebook instance

Once the instance has been started and is accessible, click on `open` to get the Jupyter notebook main page. We will begin by cloning this github repository into the notebook instance. Note that we want to make sure to clone this into the appropriate directory so that the data will be preserved between sessions.

Click on the `new` dropdown menu and select `terminal`. By default, the working directory of the terminal instance is the home directory, however, the Jupyter notebook hub's root directory is under 'SageMaker'. Enter the appropriate directory and clone the repository as follows.

    cd SageMaker
    git clone https://github.com/inigo-irigaray/sentiment-analysis-web-aws.git
    exit
    
After you've finished close the terminal window.
