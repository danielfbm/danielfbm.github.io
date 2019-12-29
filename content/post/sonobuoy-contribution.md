---
title: "My First Sonobuoy Contribution"
date: 2019-12-29T15:52:19+08:00
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

While using [Sonobuoy](sonobuoy.io) as our main test runner engine at [Alauda](alauda.cn) we noticed a small issue and decided to contribute the patch:

Sonobuoy will create [Kubernetes RBAC](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) `ClusterRole` and `ClusterRoleBinding` but will also destroy together with all the test data. This is ideal, but in the current implementation it will delete it globally affecting other parallel tests permissions, resulting in lots of permission failures. [This Pull-request](https://github.com/vmware-tanzu/sonobuoy/pull/1060) solves this issue by adding a test run `namespace` label to all `Cluster` resources, and make these resource names unique according to the `namespace`. 

Try it out and let us know. 
Happy testing!