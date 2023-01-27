---
title: Monitoring your jobs using Grafana and the Apache Spark dashboard 
slug: monitor
excerpt: Find out how to monitor your jobs using Grafana and the Apache Spark dashboard
section: Getting started
order: 2
updated: 2020-03-06
---

**Last updated 06<sup>th</sup> March, 2020**

## Objective

This guide will tell you how you can monitor you jobs after submitting them. 

In this guide, we are assuming that you're using the [OVHcloud Manager](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/sg/&ovhSubsidiary=sg){.external} to use the Data Processing platform and you have already submitted a job. 

To read an introduction about Data Processing service you can visit [Data Processing Overview](../overview){.external}.

## Requirements 

- Access to the [OVHcloud Manager](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/sg/&ovhSubsidiary=sg){.external}
- A job that has been already submitted to Data Processing

## Instructions

### Apache Spark Dashboard 

After submitting your job, follow these steps to open its Apache Spark dashboard: 

- Find your job in the list of jobs in the Data Processing page of the OVHcloud Manager.
- Click on the name of the job to open its dashboard. 

![Data Processing Job dashboard](images/jobuserinterface.png){.thumbnail}

- Click on  `Open job user interface`{.action} in the **Actions** panel to open the Apache Spark dashboard. If you do this right after submitting a job, you will see a warm up page for a few seconds while your job is starting. 

![Warming up](images/warmup.png){.thumbnail}

The Apache Spark dashboard for your job will then start automatically. 

![Apache Spark dashboard](images/sparkdashboard.png){.thumbnail}

### Grafana Dashboard

After you submit a job to the Data Processing platform, follow these steps to monitor your job using a Grafana dashboard.

- Find your job in the list of jobs in the Data Processing page in the OVHcloud Manager.
- Click on the name of the job to open its dashboard.
- In the dashboard, click on `Monitor job`{.action} in the **Actions** panel.

![Metrics token](images/token.png){.thumbnail}

- Copy and save the metrics token that is now displayed in the popup.
- Open [https://grafana.dataconvergence.ovh.com:3000/d/VhF0A_Gnz/ovhcloud-data-processing-overview?orgId=2](https://grafana.dataconvergence.ovh.com:3000/d/VhF0A_Gnz/ovhcloud-data-processing-overview?orgId=2) and login with your OVHcloud account.
- Paste the metrics token that you copied and saved before in the `token`{.action} field.
- You should now be able to see your job's dashboard if your job ID is already set in the `jobId`{.action} field.
  Otherwise, you can simply write the ID of the jobs you want to monitor in this field.
  
![grafana charts](images/grafanadashboard.png){.thumbnail}

## Go further

To learn more about using Data Processing and how to submit a job and process your data, we invite you to look at [Data Processing documentations page](../).

You can send your questions, suggestions or feedbacks in our community of users on [https://community.ovh.com/en/](https://community.ovh.com/en/){.external} or on our [Discord](https://discord.gg/VVvZg8NCQM){.external} in the channel **#dataprocessing-spark**
