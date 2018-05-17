---
layout: "opentelekomcloud"
page_title: "OpenTelekomCloud: opentelekomcloud_cce_cluster_v1  "
sidebar_current: "docs-opentelekomcloud-datasource-cce-cluster-v1"
description: |-
  Get information on CCE Cloud Container Engine.
---

# opentelekomcloud_vpc_peering_connection_accepter_v2

`opentelekomcloud_cce_cluster_v1` provides details about all clusters and obtains certificate for accessing cluster information.

## Example Usage

 ```hcl
 data "opentelekomcloud_cce_cluster_v1" "cluster_v1" { 
 id = "${opentelekomcloud_cce_cluster_v1.cluster_1.id}"
}

output "resource_data" {
  value = "${data.opentelekomcloud_cce_cluster_v1.cluster_v1.name}"
}
```

## Argument Reference

The following arguments are supported:

* `id` -  (Optional) The ID of container cluster.

* `status` - (Optional) The status of cluster.

* `az` - (Optional) The AZ where the cluster resides.

* `vpc_name` - (Optional) The name of network used by the cluster.

* `vpc_id` - (Optional) The VPC ID of container cluster.

* `type` - (Optional) The Container cluster type HA and Single. Defaults to `single`.


## Attributes Reference


* `id` - Specifies the ID of container cluster.

* `name` - Specifies the name of cluster.

* `status` - Specifies the status of cluster.

* `k8s_version` - Specifies the version of kubernetes.

* `az` - Specifies the AZ where the cluster resides.

* `cpu` - Specifies the CPU size (measured in cores) of all hosts in the cluster.

* `vpc_name` - Specifies name of the network used by the cluster.

* `vpc_id` - Specifies VPC ID of container cluster.

* `subnet_id` - Specifies Subnet ID of the container cluster.

* `endpoint` - Specifies the address used to access container cluster from the internal network.

* `external_endpoint` - Specifes the address used to access the container cluster through the external network.

* `security_group_id` - Specifies the Security group ID of container cluster.

* `type` - Container cluster type HA and Single. Default is `single`.

* `cacrt` - Specifies k8s cluster's cacrt. 
 
* `clientcrt` - Specifies k8s cluster's clientcrt.

* `clientcrt` - Specifies k8s cluster's clientcrt.

**hosts**

* `name` - Specifies name of the node.

* `id` - Specifies ID of the node.

* `private_ip` - Specifies private IP address of node.
 
* `public_ip` - Specifies public IP address of node.
 
* `flavor` - Specifications of the node to be added.

* `az` -  Specifies the AZ where the node to be added resides.

* `sshkey` - Specifies the SSH key used to create the host.

* `status` - Specifies the node current status. It is different with instance status.

**Volume**

* `diskType` - Specifies the disk type, which is used to determine a data disk or a system disk.
  
* `diskSize` - Specifies the disk size.

* `volumeType` - Specifies the disk IO type.


 


