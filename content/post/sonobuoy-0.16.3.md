---
title: "Sonobuoy v0.16.3"
date: 2019-12-14T11:59:59+08:00
draft: false
keywords:
- kubernetes
- k8s
- testing
- sonobuoy
- e2e
- docker
tags:  
- kubernetes
- testing
- sonobuoy
---

Here is the [Official website link](https://sonobuoy.io/) and the [GitHub repo](https://github.com/vmware-tanzu/sonobuoy).

**Update: version [v0.17.0](https://sonobuoy.io/docs/v0.17.0/index.html) is available**

## What is Sonobuoy?

According to the website:

> Sonobuoy is a diagnostic tool that makes it easier to understand the state of a Kubernetes cluster by running a set of plugins (including Kubernetes conformance tests) in an accessible and non-destructive manner. It is a customizable, extendable, and cluster-agnostic way to generate clear, informative reports about your cluster.

In general I see sonobuoy as a Test Framework to be executed inside Kubernetes.

## QuickStart

Run a small set of kubernetes conformance tests:

1. Install the CLI from [GitHub Releases](https://github.com/vmware-tanzu/sonobuoy/releases);
2. Have a kubernetes environment ready, I will be using the `Docker for Mac`'s kubernetes;
3. Run the quick tests command `sonobuoy run --wait --mode quick`
4. In another Terminal window: `kubectl get pods -n sonobuoy -w` to watch all pods in the sonobuoy namespace
5. `sonobuoy status` can also provide some helpful information regarding the run

Once it is done:

1. `results=$(sonobuoy retrieve)`
2. `sonobuoy results $results`

To cleanup: `sonobuoy delete --wait`

For more details on the contents of the result file, please check [Snapshot Layout](https://sonobuoy.io/docs/v0.16.3/snapshot/)

## Customizing

OK, so sonobuoy provides useful tools to run tests inside Kubernetes and includes its official `Conformance Tests`, but actually its is a very powerful tool to create very powerful custom tests for our own applications mostly because it offers a functionality called [plugins](https://sonobuoy.io/docs/v0.16.3/plugins/)

### Plugins

Run `sonobuoy gen plugin --show-default-podspec -n hello-world -i hello-world:latest` to generate our first sonobuoy plugin. This command will output a yaml file, save it as necessary.


In order to try it out, the docs provide very neat [examples](https://github.com/vmware-tanzu/sonobuoy/blob/master/examples/plugins), the [cmd-runner](https://github.com/vmware-tanzu/sonobuoy/blob/master/examples/plugins/cmd-runner) is a great place to start.



## Conclusion

When looking for a customizable and ready to go tool to run tests using `Kubernetes`, Sonobuoy is a great option for try.

