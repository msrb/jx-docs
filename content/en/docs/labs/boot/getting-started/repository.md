---
title: Create Repository
linktitle: Create Repository
description: Create a Git repository for your installation
weight: 20
---

Once you are connected to a Kubernetes cluster you need to create a git repository for your development environment.

## Creating a fresh install

To create a fresh install run the `jxl boot create` command:

``` 
jxl boot create
```

This will create the git repositories for your environments.

The command will output instructions on how to setup the [secrets](/docs/labs/boot/getting-started/secrets/) and then [run the boot job](/docs/labs/boot/getting-started/run/).


### Using Multi Cluster

If you wish to use [multi cluster](/docs/labs/boot/multi-cluster/) where your `staging` and `production` environments are in separate repositories then please add the `--env-remote` flag then follow the [multi cluster documentation](/docs/labs/boot/multi-cluster/) after you have booted your development environment.

``` 
jxl boot create --env-remote
```

This will create the git repositories for your environments.

The command will output instructions on how to setup the [secrets](/docs/labs/boot/getting-started/secrets/) and then [run the boot job](/docs/labs/boot/getting-started/run/).

## Upgrading an existing cluster
 
 
 f you have already installed Jenkins X somehow; e.g. via the deprecated `jx install` command of via `jx boot` with or without using GitOps using helm 2.x to manage the development environment then we have a way to upgrade your cluster to helm 3 and helmfile.
  
To do this connect to your current Kubernetes cluster so that `kubectl` can see the development namespace.

You can test this by running:

```
kubectl get environments 
```

Which should list the `Environment` resources in your installation which usually has `dev`, `staging` and `production`.

You can use the `jxl boot upgrade` command to help upgrade your existing Jenkins X cluster to helm 3 and helmfile.

Connect to the cluster you wish to migrate and run:

``` 
jxl boot upgrade
```

and follow the instructions.

If your cluster is using GitOps the command will clone the development git repository to a temporary directory, modify it and submit a pull request.

If your cluster is not using GitOps then a new git repository will be created along with instructions on how to setup the [secrets](/docs/labs/boot/getting-started/secrets/) and then [run the boot job](/docs/labs/boot/getting-started/run/).
