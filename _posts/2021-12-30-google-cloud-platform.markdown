---
layout: post
title:  "Test Google cloud platform!"
date:   2021-12-30 13:33:00 +0100
categories: projects
#comments: false
math: false
---

:sparkles: Started to test the Google cloud platform (GCP), as an alternative of the Microsoft Azure.

## Codelabs tested

### [A Tour of Cloud IoT Core](https://codelabs.developers.google.com/codelabs/cloud-iot-core-overview#0)

This Google codelab gives a hands-on walkthrough to setting up and configuring IoT devices using Cloud IoT Core. It will transmit telemetry messages from a device and the device will respond to configuration changes from a server based on real-time data.

Prerequisites: [Google Cloud Shell](https://cloud.google.com/shell/docs/), available in [Google Cloud Console](https://console.cloud.google.com/home/dashboard).

**Notice**: Service region matching is important, otherwise jobs like DataFlow will not be successful.

To grant access to Vertex AI to resources in the home project: [Go to the IAM page](https://console.cloud.google.com/iam-admin/iam?_ga=2.20264696.1350552028.1640899612-1010719289.1640897938)

### [Time Series Forecasting with Vertex AI and BigQuery ML](https://codelabs.developers.google.com/codelabs/time-series-forecasting-with-cloud-ai-platform?hl=en#0)

Tried to use VSCode to connect to the notebook, but it didn't work. It is possible to `ssh` to the notebook **Compute Engine**. However, there is no way to select the Jupyter kernel. The only way is still to open JupyterLab from **Vertex Workbench**.


### [Using IoT Core to Stream Heart Rate Data](https://codelabs.developers.google.com/codelabs/iotcore-heartrate?hl=en#8)

### [Kubeflow Pipelines - GitHub Issue Summarization](https://codelabs.developers.google.com/codelabs/cloud-kubeflow-pipelines-gis?hl=en)




## Other GCP services
### Enable App Engine in a Cloud project

Need to figure out how to delete an App instead of disabling it in **App Engine**.


## Marketplace
### Dataset

1. [Passive Acoustic Monitoring](https://console.cloud.google.com/marketplace/product/noaa-public/passive_acoustic_monitoring?project=true-kite-336709).


## Cloud Storage
### Data management
1. Upload and download an object to and from the Bucket
{% highlight Bash %}
export MY_BUCKET=my-project-bucket-1
wget https://cloud.google.com/storage/images/kitten.png
gsutil cp kitten.png gs://$MY_BUCKET
gsutil cp \
    gs://$MY_BUCKET/kitten.png \
    gs://$MY_BUCKET/just-a-folder/kitten3.png #download
{% endhighlight %}

## Visualization and dashboards
### [looker](https://looker.com/)
Looker can be used for real-time data visualization and beautiful analytics dashboard.

### [What-If Tool](https://pair-code.github.io/what-if-tool/)

An eye-catching beautiful tool to visualize the behavior of trained machine learning models, with minimal coding.

> Personally, prefer GCP more than Azure. Cloud shell of GCP is much better than Azure, and the virtual machine can be `SSH` connected directly from the web.