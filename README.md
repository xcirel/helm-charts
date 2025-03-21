# Helm Charts

This repository contains the Helm charts for the Kubernetes.

How to create a Helm chart and add it to the Helm repository.

## Create a New Helm Chart

```bash
helm create my-first-chart
```

## Package the Helm Chart

```bash
helm package my-first-chart
```

## Gerenerate the Index File

```bash
helm repo index --url https://raw.githubusercontent.com/xcirel/helm-charts/main/ .
```

## Add the Helm Chart to the Helm repository like GitHub

```bash
git add .
git commit -m "Add my-first-chart"
git push -u origin main
```

## Add the Helm repository

```bash
helm repo add xcirel-repo https://raw.githubusercontent.com/xcirel/helm-charts/main/
helm repo update
```

## Install the Helm Chart

```bash
helm install my-first-chart xcirel/my-first-chart -n my-first-chart --create-namespace
```

## To generate a new version of the Helm Chart

After changing the Helm Chart `Chart.yaml`, you need to package it again.

```bash
helm package my-first-chart
helm repo index --url https://raw.githubusercontent.com/xcirel/helm-charts/main/ .
```

## Publish a new Chart

```bash
helm pull prometheus-community/kube-prometheus-stack --version 69.8.0
```

Unpack the chart and copy the files to the chart folder. Made your changes and package it again.

```bash
helm package kube-prometheus-stack
helm repo index --url https://raw.githubusercontent.com/xcirel/helm-charts/main/ .
```

```bash
git add .
git commit -m "Add kube-prometheus-stack"
git push -u origin main
```
