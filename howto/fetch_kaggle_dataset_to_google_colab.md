Ref: https://medium.com/analytics-vidhya/how-to-fetch-kaggle-datasets-into-google-colab-ea682569851a

## Step 1: Get Kaggle API token
1. Go to Your Account and click on Create New API Token.
2. A file named kaggle.json is downloaded which contains the username and token key (~/.kaggle/kaggle.json to use the API)

## Step 2: Upload kaggle.json into Google Drive
1. Create a folder on drive named kaggle where the Kaggle data set will be stored
2. Upload the kaggle.json file into the Kaggle folder on drive

## Step 3: Create a new Colab notebook wher you want to import the dataset

## Step 4: Mount the drive to colab notebook using the below code to mount your google drive

```
from google.colab import drive
drive.mount('/content/gdrive')
```

Get your authorization code using the URL prompted and enter it in the response box

## Step 5: Run the following code to provide the config path to kaggle.json
```
import os
os.environ['KAGGLE_CONFIG_DIR'] = "/content/gdrive/My Drive/Kaggle"
# /content/gdrive/My Drive/Kaggle is the path where kaggle.json is present in the Google Drive
```

## Step 6: Change your present working directory

```
#changing the working directory
%cd /content/gdrive/My Drive/Kaggle
#Check the present working directory using pwd command
```

## Step 7: Download the kaggle dataset
Go to kaggle and copy the API Command to download the dataset

Your API Command will look like “kaggle datasets download -d datasnaek/youtube-new”
Run the following code using ! :
```
!kaggle datasets download -d datasnaek/youtube-new
```

You can check the content in your directory using ls command as follows:
```
!ls
```

## Step 8: Unzip your data and remove the zip file
Use the unzip and rm command
```
#unzipping the zip files and deleting the zip files
!unzip \*.zip  && rm *.zip
```

