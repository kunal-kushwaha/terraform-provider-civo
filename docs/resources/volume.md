---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "civo_volume Resource - terraform-provider-civo"
subcategory: ""
description: |-
  Provides a Civo volume which can be attached to an instance in order to provide expanded storage.
---

# civo_volume (Resource)

Provides a Civo volume which can be attached to an instance in order to provide expanded storage.

## Example Usage

```terraform
# Get network
data "civo_network" "default_network" {
    label = "Default"
}

# Create volume
resource "civo_volume" "db" {
    name = "backup-data"
    size_gb = 5
    network_id = data.civo_network.default_network.id
    depends_on = [
      data.civo_network.default_network
    ]
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- **name** (String) A name that you wish to use to refer to this volume
- **network_id** (String) The network that the volume belongs to
- **size_gb** (Number) A minimum of 1 and a maximum of your available disk space from your quota specifies the size of the volume in gigabytes

### Optional

- **id** (String) The ID of this resource.
- **region** (String) The region for the volume, if not declare we use the region in declared in the provider.

### Read-Only

- **mount_point** (String) The mount point of the volume (from instance's perspective)

## Import

Import is supported using the following syntax:

```shell
# using ID
terraform import civo_volume.db 506f78a4-e098-11e5-ad9f-000f53306ae1
```
