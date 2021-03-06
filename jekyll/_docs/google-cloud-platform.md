---
layout: classic-docs
title: Deploying to Google Cloud Platform
categories: [how-to]
description: Deploying to Google Cloud Platform
categories: [how-to]
---

## Prerequisites

Setting up continuous deployment to Google Cloud Platform is pretty straightforward. Whether you are deploying to Google App Engine, Google Managed VMs, Google Compute Engine, or Google Container Engine, you'll need to first complete some of the same prerequisites.

### gcloud

The [Google Cloud SDK](https://cloud.google.com/sdk/), or the gcloud tool, is the command line tool that can be used to deploy to any Google Cloud product. Fortunately, it comes pre-installed on CircleCI.

### Service Account Authentication

You'll need to use a GCP Service Account to authenticate the `gcloud` tool before deploying your project. See more detail on this in the [gcloud authentication doc](/docs/google-auth). You can also see a complete, working example in the [sample App Engine project](https://github.com/GoogleCloudPlatform/continuous-deployment-circle).

## Google App Engine and Managed VMs

To deploy to Google App Engine, see the [complete doc](/docs/deploy-google-app-engine) or the [sample project](https://github.com/GoogleCloudPlatform/continuous-deployment-circle).

## Google Compute Engine And Google Container Engine

Deployment processes to Compute Engine and Container Engine can vary, but the gcloud tool is usually the foundational piece for interacting with these environments. For compute engine, you can use

    gcloud compute copy-files <artifact> <instance_name:path_to_artifact>

to copy artifacts to your instance. For Container Engine, the gcloud command can download the kubectl command

    gcloud --quiet components update kubectl
    gcloud container clusters get-credentials <your-cluster>

which can then be used to interact with your Kubernetes cluster.
