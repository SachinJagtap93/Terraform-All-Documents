---
layout: "opentelekomcloud"
page_title: "OpenTelekomCloud: opentelekomcloud_cce_nodes_v1"
sidebar_current: "docs-opentelekomcloud-resource-cce_nodes-v1"
description: |-
  Add a node to a container cluster. 
---


# opentelekomcloud_cce_nodes_v1_
Add a node to a container cluster. 

## Example Usage

 ```
resource "opentelekomcloud_cce_node_v1" "node_1" {
  kind = "host"
  apiversion = "v1"
  id = "Enter cluster uuid"
  spec {
    flavor   = "Enter instance type (flavor)"
    sshkey = "click2cloud-key"

    volume=[{
      disk_type = "root"
      disk_size = 40
      volume_type = "SAS"
    },
    {
        disk_type = "data"
        disk_size = 100
        volume_type = "SATA"
    }]
  }
  replicas = 1


 ```
## Argument Reference
The following arguments are supported:


* `kind` - (Required) Kind is a string value representing the REST resource this object represents. 

* `apiVersion` - (Required) APIVersion defines the versioned schema of this representation of an object.

* `replicas` - (Required) Number of node instances to be added. A maximum of 15 nodes are allowed in a single container cluster.
 
* `name` - (Required) 	Node Name.

* `id` - (Optional) UUID is the unique in time and space value for this object.

* `spaceuuid` - (Optional) ID of the space where the user resides.

**spec - (Required)** 
    
    * `flavor` - (Required) Specifications of the node to be added.
    
    * `label` - (Optional) Label attached to the node.
    
    * `sshkey` - (Required) SSH key used to create the node.
    
    * `snat` - (Optional) Whether the SNAT function is supported. Options: true and false.
    
    * `az` - (Optional) Name of the AZ where the node to be added resides.
    
    * `tags` - (Optional) Specifies the tags of a Node.

**volume - (Required)** 
    
    * `disk_type` - (Required) Disk type, which is used to determine a data disk or a system disk. root: system disk, data: data disk.
    
    * `disk_size` - (Required) Disk size. Capacity of the system disk is hard-coded to be 40 GB. Capacity of the data disk is user configurable and ranges from 100 GB to 32768 GB (inclusive).
    
    * `volume_type` - (Required) Disk IO type. SATA: indicates SATA disks, SAS: indicates SAS disks, SSD: indicates SSD disks.
 
