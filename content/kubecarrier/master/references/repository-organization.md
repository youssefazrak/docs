---
title: Repository Organization
weight: 20
date: 2020-04-24T09:00:00+02:00
---

The [KubeCarrier repository](https://github.com/kubermatic/kubecarrier) is organized as follows:
```bash
├── cmd
│   ├── {kubectl-kubecarrier, manager, operator, ferry, catapult, elevator}
│   │   └── main.go
├── config
│   ├── dockerfiles
│   ├── internal
│   │   ├── {manager, ferry, catapult}
│   └── operator
├── docs
├── hack
├── pkg
│   ├── {cli, manager, operator, ferry, catapult, elevator}
│   │   └── internal
│   ├── apis
│   │   ├── core
│   │   ├── catalog
│   │   ├── operator
│   ├── internal
└── test
```

**cmd** contains the `main.go` for every KubeCarrier component.

**config** contains:
- **dockerfiles**: dockerfiles for building docker images for KubeCarrier components and test image.
- **operator**: configuration (CRD, Webhook, RBAC, etc) of KubeCarrier operator.
- **internal**: configuration that used within KubeCarrier's CLI and the KubeCarrier Operator to bootstrap and reconcile KubeCarrier installation, it's not meant for direct use.

**docs** contains the documentation of the KubeCarrier project.

**hack** contains some useful scripts.

**pkg** contains:
- **apis**: KubeCarrier APIs.
    - **core**: kubecarrier.io api group
    - **catalog**: catalog.kubecarrier.io api group
    - **operator**: operator.kubecarrier.io api group
- **internal**: internal packages used across components.
- **component (cli, manager, operator, ferry, catapult)**: source code for KubeCarrier components.
    - **internal**: internal packages for every component (controller, etc).

**test** contains KubeCarrier e2e tests.
