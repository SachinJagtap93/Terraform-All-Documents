---
layout: "opentelekomcloud"
page_title: "OpenTelekomCloud: opentelekomcloud_cce_cluster_v1 "
sidebar_current: "docs-opentelekomcloud-resource-cce-cluster-v1"
description: |-
  Provides Cloud Container Engine(CCE) resource.
---

# opentelekomcloud_resource_opentelekomcloud_cce_cluster_v1  

Manages a Cloud Contianer Engine(CCE) resource within OpenTelekomCloud.

## Example Usage

 ```hcl
resource "opentelekomcloud_vpc_v1" "vpc_v1" {
  name = "${var.vpc_name}"
  cidr = "${var.vpc_cidr}"
}

resource "opentelekomcloud_vpc_subnet_v1" "subnet_v1" {
  name = "${var.subnet_name}"
  cidr = "${var.subnet_cidr}"
  gateway_ip = "${var.subnet_gateway_ip}"
  vpc_id = "${opentelekomcloud_vpc_v1.vpc_v1.id}"
}

resource "opentelekomcloud_cce_cluster_v1" "cce_v1" {
kind = "cluster"
name = "${var.cce_name}"
api_version = "v1"
vpc_id = "${opentelekomcloud_vpc_v1.vpc_v1.id}"
subnet_id = "${opentelekomcloud_vpc_subnet_v1.subnet_v1.id}"
type = "Single"
description = "${var.cce_v1_description}"
publicip_id = "${var.cce_v1_publicip_id}"

}
}
```

## Argument Reference

The following arguments are supported:

- `kind` - (Required) The Kind is a string value representing REST resource.

- `apiVersion` - (Required) The APIVersion defines versioned schema of this representation of an object.

**spec - (Required)**

- `vpc_id` - (Required) The VPC ID of container cluster.

- `subnet_id` - (Required) The Subnet ID of the container cluster.

- `description` - (Optional) The description must be 0 to 200 characters in length.

- `security_group_id` - (Optional) The Security group ID of container cluster.

- `type` - (Optional) Container cluster type HA and Single. Defaults to `single`.

- `publicip_id` - (Optional) The Unique ID of an EIP bound to the container cluster.

**metadata - (Required)**

- `name` - (Required) The name of cluster must be 0 to 24 characters in length. Cluster name must start with a lowercase letter and contain only lowercase letters, digits, and hyphens.


## Attributes Reference


The following attributes are exported:

* `id` -  Specifies the ID of container cluster.

* `status` -  Specifies the status of cluster.

* `k8s_version` - Specifies the version of kubernetes.

* `az` - Specifies the AZ where the cluster resides.

* `cpu` - Specifies the CPU size (measured in cores) of all hosts in the cluster.

* `vpc_name` - Specifies name of the network used by the cluster.

* `endpoint` -  Specifies the address used to access container cluster from the internal network.

* `external_endpoint` -  Specifes the address used to access the container cluster through the external network.

* `type` - See Argument Reference above.

**`hosts`** 

* `name` - Specifies name of the node.

* `id` - Specifies ID of the node.

* `private_ip` - Specifies private IP address of node.

* `public_ip` - Specifies public IP address of node.

* `flavor` - Specifications of the node to be added.

* `az` -  Specifies the AZ where the node to be added resides.

* `sshkey` - Specifies the SSH key used to create the host.

* `status` - Specifies the node current status. It is different with instance status.

## Import

Clusters can be imported using the name, e.g.

```
$ terraform import opentelekomcloud_cce_cluster_v1 7117d38e-4c8f-4624-a505-bd96b97d024c
```
