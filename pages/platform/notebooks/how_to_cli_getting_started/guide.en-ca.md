---
title: Getting started
slug: getting-started-cli
excerpt: Learn how to run an AI Training notebook using the CLI
section: How to (with CLI)
order: 1
---
*Last updated 27th of May, 2021.*

## Objective

This guide covers the submission of [**notebooks**](../definition) through the **ovhai** CLI.

## Requirements

-   a working `ovhai` CLI ([how to install ovhai CLI](../../ai-training/install-client))

## Instructions

### Run a new notebook

First, you need to select one of the machine learning frameworks and an editor among those available. You can
get a list of them using the `ovhai capability framework` and `ovhai capability editor` commands:

``` {.console}
$ ovhai capability framework
ID                       NAME                       DOCURL                                     VERSIONS
fastai                   fastai Course              https://docs.fast.ai/                      2.2.5   
pytorch                  PyTorch                    https://pytorch.org/docs/stable/index.html 1.8.1   
mxnet                    MXNet                      https://mxnet.apache.org/versions/1.5.0/   1.5.0   
tensorflow               Tensorflow                 https://www.tensorflow.org/api_docs        2.4.1   
huggingface-transformers Hugging Face Transformers  https://huggingface.co/transformers/       4.5.0   
one-for-all              One image to rule them all                                            v98     
autogluon-mxnet          AutoGluon + MXNet                                                     0.1.0   

$ ovhai capability editor
ID         NAME       DOCURL                                      
vscode     VSCode     https://code.visualstudio.com/docs          
jupyterlab JupyterLab https://jupyterlab.readthedocs.io/en/stable/
```

In our example, we will create a new notebook using PyTorch and JupyterLab, with 1 GPU:

``` {.console}
$ ovhai notebook run --gpu 1 pytorch jupyterlab                                                                                                                                                                                  14:37:13

id: fa43cdad-97cc-46e7-ac3b-31dd1d7d5a1e
createdAt: "2021-05-27T12:37:14.752980089Z"
updatedAt: "2021-05-27T12:37:14.752980089Z"
user: user-6quQBpkve6AT
spec:
  name: ""
  labels: {}
  resources:
    gpu: 1
    gpuModel: Tesla-V100S
    cpu: 13
  volumes: []
  unsecureHttp: false
  env:
    frameworkId: pytorch
    frameworkVersion: 1.8.1
    editorId: jupyterlab
status:
  lastTransitionDate: ~
  infos: ~
  state: STARTING
  duration: 0
  url: ~
  monitoringUrl: ~
  lastStartedAt: ~
  lastStoppedAt: ~
  dataSync: []
```

The first line in the output shows the ID of the notebook, here it is `fa43cdad-97cc-46e7-ac3b-31dd1d7d5a1e`.

If you don't have the ID of the notebook you want to access, you can list all your notebooks using:

``` {.console}
$ ovhai notebook ls
```

We need to wait a few seconds for the notebook to start. You can get the notebook information again using its ID:

``` {.console}
$ ovhai notebook get fa43cdad-97cc-46e7-ac3b-31dd1d7d5a1e

Name:
ID:         fa43cdad-97cc-46e7-ac3b-31dd1d7d5a1e
Created At: 27-05-21 12:37
Updated At: 27-05-21 12:37
User:       user-6quQBpkve6AT
Spec:
  Resources:
    GPU:       1
    GPU Model: Tesla-V100S
    CPU:       13
  Volumes:
  Labels:
  Unsecure: false
  Env:
    Framework ID:    pytorch
    Framework Version: 1.8.1
    Editor ID:       jupyterlab
Status:
  State:           RUNNING
  Infos:
  Transitioned At:
  Duration:        67s
  Url:             https://fa43cdad-97cc-46e7-ac3b-31dd1d7d5a1e.notebook.gra.training.ai.cloud.ovh.net
  Monitoring Url:  https://monitoring.gra.training.ai.cloud.ovh.net/d/gpu?var-notebook=fa43cdad-97cc-46e7-ac3b-31dd1d7d5a1e&from=1622118974763
  Transitioned At: 27-05-21 12:37
```

Now that the notebook is in the `RUNNING` state, a https address is defined in the Url field. This URL corresponds to your JupyterLab server. Pasting this URL in your browser displays the following screen:

![image](images/jupyterlab_home_page.png)

You can now start writing code in your notebook. Since we used the PyTorch framework in our example, we will be able to use it without having to install anything ourselves.

Once you are done with your notebook, you can stop it with the command below:

``` {.console}
$ ovhai notebook stop fa43cdad-97cc-46e7-ac3b-31dd1d7d5a1e
```

Stopping a notebook will make it unavailable from your browser, and start synchronizing volumes mounted with `RW` permissions to your object storage.

Once the synchronization is finished, and the notebook state is `STOPPED`, you can either start it again or delete it.

Being able to restart a notebook is one of the main differences compared to using [jobs](../../ai-training/jobs). Restarting a notebook will restore your notebook code as it was when you stopped it. However, you will need to re-run your code to reload your variables because the program state is not saved.
To restart a notebook, run this command:

``` {.console}
$ ovhai notebook start fa43cdad-97cc-46e7-ac3b-31dd1d7d5a1e
```

You are billed for `RUNNING` notebooks but not for `STARTING`, `STOPPING` and `STOPPED` notebooks.
However, to restore your code when you restart a `STOPPED` notebook, it needs to be stored in your object storage, which you are billed for.

This is useful when you work on a notebook for some time. If you know you will not use a notebook anymore and want to remove the notebook state from your object storage, you need to delete the notebook:

``` {.console}
$ ovhai notebook delete fa43cdad-97cc-46e7-ac3b-31dd1d7d5a1e
```

Note that a notebook must first be stopped before being deleted, and that deleted notebook cannot be restarted.

## Going further

Learn how to access your object storage data from your notebooks [here](../data).

Learn how to share your notebooks with other people [here](../sharing-notebooks).

## Feedback

Please send us your questions, feedback and suggestions to improve the service:

-   On the OVHcloud [AI community forum](https://community.ovh.com/en/c/Data-AI)
