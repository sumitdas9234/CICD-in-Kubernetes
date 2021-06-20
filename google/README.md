# Getting Started

Last Updated: Jun 18, 2021 11:15 PM
Status: Progress


## Getting the Custom Docker Image

We shall be using a custom docker image built on top of a few popular tools :

```bash
# Pull the image from DockerHub
# Mount your current working directory on the docker container by default
docker run -it --rm -v ${PWD}:/work -w /work sumitdas9234/gcp-k8s-alpine:latest
```

## Authenticating with Google Cloud Platform

```bash
# follow the prompt (get yourself a free trial, if needed)
gcloud auth login
```

## Setting up your GCP Account

```bash
# Create a fresh project named "Kubernetes"
gcloud projects create --name="Kubernetes" --set-as-default
# Enable the Google Containers API, Google Compute API
gcloud services enable compute.googleapis.com container.googleapis.com
```

## Creating a Kubernetes Cluster Using CLI

```bash
gcloud container clusters create k8s-cluster \
--disk-size 50 \
--num-nodes 1 \
--machine-type e2-small \
--no-enable-cloud-logging \
--no-enable-cloud-monitoring  \
--zone us-east4-b
```

## Accessing the Cluster

```bash
gcloud container clusters get-credentials k8s-cluster --zone us-east4-b
```