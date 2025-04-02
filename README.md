# Helm Charts

This repository contains the Helm charts for the Kubernetes.

How to create a Helm chart and add it to the Helm repository.

## Create a New Helm Chart

```bash
helm create charts/my-app
```

## Package the Helm Chart

```bash
helm package charts/my-app --destination ./packages
```

## Gerenerate the Index File

```bash
helm repo index . --url https://raw.githubusercontent.com/xcirel/helm-charts/main
```

## Add the Helm Chart to the Helm repository like GitHub

```bash
git add .
git commit -m "Add my-app"
git push -u origin main
```

## Add the Helm repository

```bash
helm repo add xcirel https://raw.githubusercontent.com/xcirel/helm-charts/main
helm repo update
```

## Install the Helm Chart

```bash
helm install my-app-chart xcirel/my-app -n my-app-chart --create-namespace
```

## To generate a new version of the Helm Chart

After changing the Helm Chart `Chart.yaml`, you need to package it again.

```bash
helm package charts/my-app
helm repo index . --url https://raw.githubusercontent.com/xcirel/helm-charts/main
```

## Publish a new Chart

For example, if you want to publish the `kube-prometheus-stack` chart, you can do it like this:

```bash
helm pull prometheus-community/kube-prometheus-stack --version 69.8.0
```

Unpack the chart and copy the files to the chart folder. Made your changes and package it again.

```bash
helm package kube-prometheus-stack
helm repo index . --url https://raw.githubusercontent.com/xcirel/helm-charts/main/
```

```bash
git add .
git commit -m "Add kube-prometheus-stack"
git push -u origin main
```
