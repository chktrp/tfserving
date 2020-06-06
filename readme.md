# Deploy TF serving on Windows with docker-compose.yml

From this guide: https://medium.com/tensorflow/serving-ml-quickly-with-tensorflow-serving-and-docker-7df7094aa008

## Deployment

1. Download TensorFlow serving image 

```docker pull tensorflow/serving```

2. Download model from 

```https://storage.googleapis.com/download.tensorflow.org/models/official/20181001_resnet/savedmodels/resnet_v2_fp32_savedmodel_NHWC_jpg.tar.gz``` 

and extract its content into `resnet\` folder.

3. The extracted files should have structure similar to this

```
resnet\
|- 1538687457\
  |- variables\
    |- variable.data-00000-of-00001
    |- variables.index
  |- saved_model.pb
```

4. Start the service with 

```docker-compose up --build``` 


## Prediction
1. Download test script from

```https://raw.githubusercontent.com/tensorflow/serving/master/tensorflow_serving/example/resnet_client.py```

2. Install Python dependencies with

```pip install -r requirements.txt```

3. Run the script

```python resnet_client.py```

## Debugging
It is possible to have an error during the container creation: `Filesharing has been cancelled`

To fix it, add the working folder to the File Sharing for Docker Desktop.

