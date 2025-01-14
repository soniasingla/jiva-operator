
# OpenEBS Jiva

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
![Release Charts](https://github.com/openebs/jiva-operator/workflows/Release%20Charts/badge.svg?branch=master)
![Chart Lint and Test](https://github.com/openebs/jiva-operator/workflows/Chart%20Lint%20and%20Test/badge.svg)

OpenEBS Jiva helm chart for Kubernetes. This chart bootstraps OpenEBS jiva operators and csi driver deployment on a [Kubernetes](http://kubernetes.io) cluster using the  [Helm](https://helm.sh) package manager

**Homepage:** <http://www.openebs.io/>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| prateekpandey14 | prateek.pandey@mayadata.io |  |
| shubham14bajpai | shubham.bajpai@mayadata.io |  |

## Get Repo Info

```console
helm repo add openebs-jiva https://openebs.github.io/jiva-operator
helm repo update
```

_See [helm repo](https://helm.sh/docs/helm/helm_repo/) for command documentation._

## Install Chart

Please visit the [link](https://openebs.github.io/jiva-operator) for install instructions via helm3.

```console
# Helm
$ helm install [RELEASE_NAME] openebs-jiva/jiva
```

_See [configuration](#configuration) below._

_See [helm install](https://helm.sh/docs/helm/helm_install/) for command documentation._


## Dependencies

By default this chart installs additional, dependent charts:

| Repository | Name | Version |
|------------|------|---------|
| https://openebs.github.io/dynamic-localpv-provisioner | localpv-provisioner | 2.8.0 |


To disable the dependency during installation, set `openebsLocalpv.enabled` to `false`.

```bash
helm install <your-relase-name> openebs-jiva/jiva --set openebsLocalpv.enabled=false
```

For more details on dependency see [Jiva chart readme](https://github.com/openebs/jiva-operator/blob/master/deploy/helm/charts/README.md).

_See [helm dependency](https://helm.sh/docs/helm/helm_dependency/) for command documentation._

## Uninstall Chart

```console
# Helm
$ helm uninstall [RELEASE_NAME]
```

This removes all the Kubernetes components associated with the chart and deletes the release.

_See [helm uninstall](https://helm.sh/docs/helm/helm_uninstall/) for command documentation._

## Upgrading Chart

```console
# Helm
$ helm upgrade [RELEASE_NAME] [CHART] --install
```

## Configuration

The following table lists the configurable parameters of the OpenEBS Jiva chart and their default values.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| csiController.annotations | object | `{}` | CSI controller annotations |
| csiController.attacher.image.pullPolicy | string | `"IfNotPresent"` | CSI attacher image pull policy |
| csiController.attacher.image.registry | string | `"k8s.gcr.io/"` |  CSI attacher image registry |
| csiController.attacher.image.repository | string | `"k8scsi/csi-attacher"` |  CSI attacher image repo |
| csiController.attacher.image.tag | string | `"v3.1.0"` | CSI attacher image tag |
| csiController.attacher.name | string | `"csi-attacher"` |  CSI attacher container name|
| csiController.componentName | string | `""` | CSI controller component name |
| csiController.driverRegistrar.image.pullPolicy | string | `"IfNotPresent"` | CSI driver registrar image pull policy  |
| csiController.driverRegistrar.image.registry | string | `"k8s.gcr.io/"` | CSI driver registrar image registry |
| csiController.driverRegistrar.image.repository | string | `"k8scsi/csi-cluster-driver-registrar"` | CSI driver registrar image repo |
| csiController.driverRegistrar.image.tag | string | `"v1.0.1"` |  CSI driver registrar image tag|
| csiController.driverRegistrar.name | string | `"csi-cluster-driver-registrar"` | CSI driver registrar container name  |
| csiController.livenessprobe.image.pullPolicy | string | `"IfNotPresent"` | CSI livenessprobe image pull policy |
| csiController.livenessprobe.image.registry | string | `"k8s.gcr.io/"` |  CSI livenessprobe image registry |
| csiController.livenessprobe.image.repository | string | `"k8scsi/livenessprobe"` |  CSI livenessprobe image repo |
| csiController.livenessprobe.image.tag | string | `"v2.2.0"` | CSI livenessprobe image tag |
| csiController.livenessprobe.name | string | `"liveness-probe"` |  CSI livenessprobe container name|
| csiController.nodeSelector | object | `{}` |  CSI controller pod node selector |
| csiController.podAnnotations | object | `{}` | CSI controller pod annotations |
| csiController.provisioner.image.pullPolicy | string | `"IfNotPresent"` | CSI provisioner image pull policy |
| csiController.provisioner.image.registry | string | `"k8s.gcr.io/"` | CSI provisioner image pull registry |
| csiController.provisioner.image.repository | string | `"k8scsi/csi-provisioner"` | CSI provisioner image pull repository |
| csiController.provisioner.image.tag | string | `"v2.1.0"` | CSI provisioner image tag |
| csiController.provisioner.name | string | `"csi-provisioner"` | CSI provisioner container name |
| csiController.resizer.image.pullPolicy | string | `"IfNotPresent"` | CSI resizer image pull policy  |
| csiController.resizer.image.registry | string | `"k8s.gcr.io/"` | CSI resizer image registry |
| csiController.resizer.image.repository | string | `"k8scsi/csi-resizer"` |  CSI resizer image repository|
| csiController.resizer.image.tag | string | `"v1.1.0"` | CSI resizer image tag |
| csiController.resizer.name | string | `"csi-resizer"` | CSI resizer container name |
| csiController.resources | object | `{}` | CSI controller container resources |
| csiController.securityContext | object | `{}` | CSI controller security context |
| csiController.tolerations | list | `[]` | CSI controller pod tolerations |
| csiNode.annotations | object | `{}` | CSI Node annotations |
| csiNode.componentName | string | `"openebs-jiva-csi-node"` | CSI Node component name |
| csiNode.driverRegistrar.image.pullPolicy | string | `"IfNotPresent"` | CSI Node driver registrar image pull policy|
| csiNode.driverRegistrar.image.registry | string | `"k8s.gcr.io/"` | CSI Node driver registrar image registry |
| csiNode.driverRegistrar.image.repository | string | `"k8scsi/csi-node-driver-registrar"` | CSI Node driver registrar image repository |
| csiNode.driverRegistrar.image.tag | string | `"v2.0.1"` |  CSI Node driver registrar image tag|
| csiNode.driverRegistrar.name | string | `"csi-node-driver-registrar"` | CSI Node driver registrar container name |
| csiNode.kubeletDir | string | `"/var/lib/kubelet/"` | Kubelet root dir |
| csiNode.labels | object | `{}` | CSI Node pod labels |
| csiNode.nodeSelector | object | `{}` |   CSI Node pod nodeSelector |
| csiNode.podAnnotations | object | `{}` | CSI Node pod annotations |
| csiNode.resources | object | `{}` | CSI Node pod resources |
| csiNode.securityContext | object | `{}` | CSI Node pod security context |
| csiNode.tolerations | list | `[]` | CSI Node pod tolerations |
| csiNode.updateStrategy.type | string | `"RollingUpdate"` | CSI Node daemonset update strategy |
| csiNode.livenessprobe.image.pullPolicy | string | `"IfNotPresent"` | CSI livenessprobe image pull policy |
| csiNode.livenessprobe.image.registry | string | `"k8s.gcr.io/"` |  CSI livenessprobe image registry |
| csiNode.livenessprobe.image.repository | string | `"k8scsi/livenessprobe"` |  CSI livenessprobe image repo |
| csiNode.livenessprobe.image.tag | string | `"v2.2.0"` | CSI livenessprobe image tag |
| csiNode.livenessprobe.name | string | `"liveness-probe"` |  CSI livenessprobe container name|
| jivaOperator.annotations | object | `{}` | Jiva operator annotations |
| jivaOperator.componentName | string | `"jiva-operator"` | Jiva operator component name |
| jivaOperator.image.pullPolicy | string | `"IfNotPresent"` | Jiva operator image pull policy |
| jivaOperator.image.registry | string | `nil` | Jiva operator image registry |
| jivaOperator.image.repository | string | `"openebs/jiva-operator"` | Jiva operator image repository |
| jivaOperator.image.tag | string | `"2.8.0"` |  Jiva operator image tag |
| jivaOperator.nodeSelector | object | `{}` |  Jiva operator pod nodeSelector|
| jivaOperator.podAnnotations | object | `{}` | Jiva operator pod annotations |
| jivaOperator.resources | object | `{}` | Jiva operator pod resources |
| jivaOperator.securityContext | object | `{}` | Jiva operator security context |
| jivaOperator.tolerations | list | `[]` | Jiva operator pod tolerations |
| jivaCSIPlugin.image.pullPolicy | string | `"IfNotPresent"` | Jiva CSI driver image pull policy |
| jivaCSIPlugin.image.registry | string | `nil` | Jiva CSI driver image registry |
| jivaCSIPlugin.image.repository | string | `"openebs/jiva-csi"` |  Jiva CSI driver image repository |
| jivaCSIPlugin.image.tag | string | `"2.8.0"` | Jiva CSI driver image tag |
| jivaCSIPlugin.name | string | `"jiva-csi-plugin"` | Jiva CSI driver container name |
| jivaCSIPlugin.remount | string | `"true"` | Jiva CSI driver remount feature, enabled by default |
| rbac.create | bool | `true` | Enable RBAC |
| rbac.pspEnabled | bool | `false` | Enable PodSecurityPolicy |
| release.version | string | `"2.8.0"` | Openebs CStor release version |
| serviceAccount.annotations | object | `{}` | Service Account annotations |
| serviceAccount.csiController.create | bool | `true` | Enable CSI Controller ServiceAccount |
| serviceAccount.csiController.name | string | `"openebs-jiva-csi-controller-sa"` | CSI Controller ServiceAccount name |
| serviceAccount.csiNode.create | bool | `true` | Enable CSI Node ServiceAccount |
| serviceAccount.csiNode.name | string | `"openebs-jiva-csi-node-sa"` | CSI Node ServiceAccount name |
| serviceAccount.jivaOperator.create | bool | `true` | Enable Jiva Operator Node ServiceAccount |
| serviceAccount.jivaOperator.name | string | `"openebs-jiva-operator"` | Jiva Operator ServiceAccount name |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
helm install  <your-relase-name> -f values.yaml  openebs-jiva/jiva
```

> **Tip**: You can use the default [values.yaml](values.yaml)
