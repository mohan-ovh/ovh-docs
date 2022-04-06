---
title: AI Training - Tutorial - Deploy a web service for YOLOv5 using Flask
slug: training/web-service-yolov5
excerpt: How to deploy a web service for YOLOv5 using your own weights with Flask
section: AI Training tutorials
order: 09
---

**Last updated 04th of October, 2021.**

## Objective

The purpose of this tutorial is to show how to deploy a web service for YOLOv5 using your own weights generated after training a YOLOv5 model on your dataset.

In order to do this, you will use [Flask](https://flask.palletsprojects.com/en/2.0.x/), an open-source micro framework for web development in Python. You will also learn how to build and use a custom Docker image for a Flask application.

For more information on how to train YOLOv5 on a custom dataset, refer to the following [documentation](https://docs.ovh.com/ie/en/publiccloud/ai/notebooks/yolov5-example/).

## Requirements

-   access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie)
-   an AI Training project created inside a Public Cloud project
-   a [user for AI Training](https://docs.ovh.com/ie/en/publiccloud/ai/users)
-   [Docker](https://www.docker.com/get-started) installed on your local computer
-   some knowledge about building image and [Dockerfile](https://docs.docker.com/engine/reference/builder/)
-   your weights obtained from training a YOLOv5 model on your dataset (refer to the *"Export trained weights for future inference"* part of the [notebook for YOLOv5](https://github.com/ovh/ai-training-examples/blob/main/notebooks/pytorch/tuto/notebook_object_detection_yolov5.ipynb))

## Instructions

First, the tree structure of your folder should be as follows.

![image](images/tree_yolov5_web_service.png){.thumbnail}

-   You have to create the folder named `models_train` and this is where you can store the weights generated after your trainings. You are free to put as many weight files as you want in the `models_train` folder.

-   Here we will mainly discuss how to write the `app.py` code, the `requirements.txt` file and the `Dockerfile`. If you want to see the whole code, please refer to the [GitHub](https://github.com/ovh/ai-training-examples/tree/main/jobs/yolov5-web-service) repository.

### Write the Flask application

Create a Python file named `app.py`.

Inside that file, import your required modules:

``` {.python}
import io
from PIL import Image
import cv2
import torch
from flask import Flask, render_template, request, make_response
from werkzeug.exceptions import BadRequest
import os
```

Create Flask app:

``` {.python}
app = Flask(__name__)
```

Load your own weights:

Here a python dictionary is created to store the name of each of your weight files (key) and the corresponding model (value).

``` {.python}
# create a python dictionary for your models d = {<key>: <value>, <key>: <value>, ..., <key>: <value>}
dictOfModels = {}
# create a list of keys to use them in the select part of the html code
listOfKeys = []
for r, d, f in os.walk("models_train"):
    for file in f:
        if ".pt" in file:
            # example: file = "model1.pt"
            # the path of each model: os.path.join(r, file)
            dictOfModels[os.path.splitext(file)[0]] = torch.hub.load('ultralytics/yolov5', 'custom', path=os.path.join(r, file), force_reload=True)
            # you would obtain: dictOfModels = {"model1" : model1 , etc}
    for key in dictOfModels :
        listOfKeys.append(key)     # put all the keys in the listOfKeys
    print(listOfKeys)
```

Write the inference function:

``` {.python}
def get_prediction(img_bytes,model):
    img = Image.open(io.BytesIO(img_bytes))
    # inference
    results = model(img, size=640)  
    return results
```

Define the GET method:

``` {.python}
@app.route('/', methods=['GET'])
def get():
  # in the select we will have each key of the list in option
  return render_template("index.html", len = len(listOfKeys), listOfKeys = listOfKeys)
```

Define the POST method:

``` {.python}
@app.route('/', methods=['POST'])
def predict():
    file = extract_img(request)
    img_bytes = file.read()
    # choice of the model
    results = get_prediction(img_bytes,dictOfModels[request.form.get("model_choice")])
    print(f'User selected model : {request.form.get("model_choice")}')
    # updates results.imgs with boxes and labels
    results.render()
    # encoding the resulting image and return it
    for img in results.imgs:
        RGB_img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
        im_arr = cv2.imencode('.jpg', RGB_img)[1]
        response = make_response(im_arr.tobytes())
        response.headers['Content-Type'] = 'image/jpeg'
    # return your image with boxes and labels
    return response

def extract_img(request):
    # checking if image uploaded is valid
    if 'file' not in request.files:
        raise BadRequest("Missing file parameter!")
    file = request.files['file']
    if file.filename == '':
        raise BadRequest("Given file is invalid")
    return file
```

Start your app:

``` {.python}
if __name__ == '__main__':
    app.run(debug=True,host='0.0.0.0')
```

Find more information about the Flask application [here](https://flask.palletsprojects.com/en/2.0.x/quickstart/#a-minimal-application) to get ready to use it.

### Write the requirements.txt file for the application

The `requirements.txt` file will allow us to write all the modules needed to make our application work. This file will be useful when writing the `Dockerfile`.

``` {.console}
Flask==1.1.2

pandas

opencv-python-headless

matplotlib

seaborn
```

### Write the Dockerfile for the application

Your Dockerfile should start with the the `FROM` instruction indicating the parent image to use. In our case we choose to start from a pytorch image:

``` {.console}
FROM pytorch/pytorch
```

Create the home directory and add your files to it:

``` {.console}
WORKDIR /workspace
ADD . /workspace
```

Install the `requirements.txt` file which contains your needed Python modules using a `pip install ...` command:

``` {.console}
RUN pip install -r requirements.txt
```

Define your default launching command to start the application:

``` {.console}
CMD [ "python" , "/workspace/app.py" ]
```

Give correct access rights to **ovhcloud user** (`42420:42420`):

``` {.console}
RUN chown -R 42420:42420 /workspace
ENV HOME=/workspace
```

### Build the Docker image from the Dockerfile

Launch the following command from the **Dockerfile** directory to build your application image:

``` {.console}
docker build . -t yolov5_web:latest
```

> [!primary]
>
> The dot `.` argument indicates that your build context (place of the **Dockerfile** and other needed files) is the current directory.

> [!primary]
>
> The `-t` argument allows you to choose the identifier to give to your image. Usually image identifiers are composed of a **name** and a **version tag** `<name>:<version>`. For this example we chose **yolov5_web:latest**.

### Test it locally (optional)

Launch the following **Docker command** to launch your application locally on your computer:

``` {.console}
docker run --rm -it -p 5000:5000 --user=42420:42420 yolov5_web:latest
```

> [!primary]
>
> The `-p 5000:5000` argument indicates that you want to execute a port redirection from the port **5000** of your local machine into the port **5000** of the Docker container. The port **5000** is the default port used by **Flask** applications.

> [!warning]
>
> Don't forget the `--user=42420:42420` argument if you want to simulate the exact same behaviour that will occur on **AI TRAINING jobs**. It executes the Docker container as the specific OVHcloud user (user **42420:42420**).

Once started, your application should be available on `http://localhost:5000`.

### Push the image into the shared registry

> [!warning]
>
> The shared registry of AI Training should only be used for testing purpose. Please consider attaching your own Docker registry. More information about this can be found [here](https://docs.ovh.com/ie/en/publiccloud/ai/training/add-private-registry).

Find the adress of your shared registry by launching this command:

``` {.console}
ovhai registry list
```

Login on the shared registry with your usual openstack credentials:

``` {.console}
docker login -u <user> -p <password> <shared-registry-address>
```

Push the compiled image into the shared registry:

``` {.console}
docker tag yolov5_web:latest <shared-registry-address>/yolov5_web:latest
docker push <shared-registry-address>/yolov5_web:latest
```

### Launch the job

The following command starts a new job running your Flask application:

``` {.console}
ovhai job run --default-http-port 5000 --cpu 4 <shared-registry-address>/yolov5_web:latest
```

> [!primary]
>
> `--default-http-port 5000` indicates that the port to reach on the job URL is the `5000`.

> [!primary]
>
> `--cpu 4` indicates that we request 4 CPUs for that job.

> [!primary]
>
> Consider adding the `--unsecure-http` attribute if you want your application to be reachable without any authentication.

## Feedback

Please send us your questions, feedback and suggestions to improve the service:

- On the OVHcloud [Discord server](https://discord.com/invite/vXVurFfwe9) 
