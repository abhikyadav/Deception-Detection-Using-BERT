# Deception-Detection-Using-BERT
# Overview
This project tries to classify tweets as real or fake depending on the tweet text and also the text present in the article that is tagged in the tweet. This particular implementation uses BERT for classification.
# Build Steps
* Follow these steps to build this project in your local system:
   * Install all the dependencies using the requirements.txt file
   * The data_preparation notebook is used to create the final training dataset. You can directly extact the data zip file and find the training dataset there. You can also upload this folder to Azure using the upload_data script
   * Next, you could add any more data to the existing dataset and can use this combined data to train your BERT model in your local using the train notebook. This noteboook is a direct adaptation of this notebook built by Prateek Joshi (https://github.com/prateekjoshi565/Fine-Tuning-BERT).
Conversely, you can also train the model on Azure using the run-training-script file which internally runs the train script in the src folder.
   * Once the model is ready you can register the model in Azure and can then build you echo_score script where you write the code to initialize your model and generate predictions.
   * This script will be used while deploying your model using the deploy script. Note that the existing code currently deploys code on Azure Container Instances, but you can also deploy it on Azure Kubernetes Services with minimal code change.
   * Once all these steps are done, you have an ACI endpoint ready which you can then use to generate predictions directly for your test data.
   * Next, you need to build your inference pipeline. In this case, the predict script is the one that takes in data from blob storage and generates predictions for that file. In case you have a dataset that you wish to generate predictions for, you could use the inference script instead.
  * I also have a receiver script which waits for a message from the data extraction pipeline (handled by a different team member) and runs the predict script whenever data for any request is ready in the blob storage. This script might not be useful for someone not related to the project.
# Dataset Used
* LIAR
* ISOT Fake News
* Buzzfeed Political News Data
* Russian Troll tweets
* Fake news dataset by UTK Machine Learning Club
* Kaggle Fake News Detection
* NBC Election Troll Tweets 2016
* Fake News on Twitter 2016 viral tweets
