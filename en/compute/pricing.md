---
editable: false
---
# Pricing [!KEYREF compute-full-name]

## What goes into the cost of using [!KEYREF compute-short-name] {#rules}

The cost of [!KEYREF compute-short-name] usage is based on:

* Computing resources
    * Type and number of cores (vCPU)
    * Amount of memory (RAM)
* Operating systems
* Type and size of storage:
    * Disks
    * Images
    * Snapshots
* The amount of outgoing traffic.
* Public IP address.

[!INCLUDE [pricing-gb-size](../_includes/pricing-gb-size.md)]

### Use of VM instances {#instance}

The cost of a VM depends on the allocated computing resources, operating system, and usage time. Attached disks and network usage are charged separately.

The cost is calculated for the time of using the VM, from the moment it is started (when its status changes to `RUNNING`) and to a complete stop. The time when the VM is stopped is not charged.

The VM starts automatically once it is created.

When creating a VM, you can specify a public IP address for it.
For information about charges for using an external IP address, see the section [[!TITLE]](../vpc/pricing.md) in the Yandex Virtual Private Cloud documentation.

#### Computing resources {#instance-resources}

When creating a VM, you specify the number of vCPUs, the basic level of core performance, and the amount of RAM in GB. For more information, see the section [[!TITLE]](concepts/vm-platforms.md).

The baseline core performance level depends on the type of [platform](concepts/vm-platforms.md).

[!KEYREF price-per-hour-count-per-second]

#### Operating systems {#burstable-instance-os}

OS usage on a VM is charged, as well. The cost depends on the OS license and the amount of computing resources. The core usage type selected for the VM also matters.

[!KEYREF price-per-hour-count-per-second]

#### Example of cost calculation

Compare costs using virtual machines with diferents levels of core performance.

Two VMs are running Linux OS:

* 5% vCPU, 1 GB RAM.
* 100% vCPU, 1 GB RAM.

Both VMs have been running for 30 days.

Cost of the virtual machine with 5% core usage:

> 5% of vCPU = ₽0.1932/hour * 30 days * 24 hours = 139.1040 ₽
>
> 1 GB RAM = ₽0.2441/hour * 30 days * 24 hours = 175.7520 ₽
>
> Total: 314.8560 ₽

Cost of the virtual machine with 100% core usage:

> 1 vCPU = ₽0.7017/hour * 30 days * 24 hours = 505.2240 ₽
>
>1 GB RAM = ₽0.2441/hour * 30 days * 24 hours = 175.7520 ₽
>
>Total: 680.9760 ₽

The cost of a VM with 5% core usage is about half as much as a VM with 100% core usage.

### Use of storage (disks, snapshots, and images) {#disk}

When creating a disk, you specify its size, that is, the amount of block storage that the disk occupies. The cost of the service depends on the time between the disk's creation and deletion, the amount of disk space, and the disk type selected during its creation.

You are charged for your disks regardless of whether the VM is running.

If you created an image or snapshot, you pay for the storage of this object separately depending on its size.

The cost is specified for one month of use. Charging per second.

## Price list {#prices}

### Computing resources  {#prices-instance-resources}

- Platform Intel Broadwell:

    | Computing resources | Cost of 1 hour, without VAT | Cost of 1 hour, with VAT |
    | ----- | ----- | ----- |
    | 5%+ of vCPU | 0.1610 ₽ | 0.1932 ₽ |
    | 20%+ vCPU | 0,4583 ₽ | 0,5500 ₽ |
    | 100% of vCPU | 0.5847 ₽ | 0.7017 ₽ |
    | RAM (for 1 GB) | 0.2034 ₽ | 0.2441 ₽ |

- Platform Intel Cascade Lake:

    | Computing resources | Cost of 1 hour, without VAT | Cost of 1 hour, with VAT |
    | ----- | ----- | ----- |
    | 5%+ of vCPU | 0.0850 ₽ | 0.1020 ₽ |
    | 20%+ vCPU | 0.2550 ₽ | 0.3060 ₽ |
    | 50%+ vCPU | 0.3740 ₽ | 0.4488 ₽ |
    | 100% of vCPU | 0.6230 ₽ | 0.7476 ₽ |
    | RAM (for 1 GB) | 0.1650 ₽ | 0.1980 ₽ |

### Computing resources of preemptible VMs {#prices-preemptible-instance-resources}

- Platform Intel Broadwell:

    | Computing resources | Cost of 1 hour, without VAT | Cost of 1 hour, with VAT |
    | ----- | ----- | ----- |
    | 5%+ of vCPU | 0.0998 ₽ | 0.1198 ₽ |
    | 20%+ vCPU | 0,2840 ₽ | 0,3408 ₽ |
    | 100% of vCPU | 0.1800 ₽ | 0.2160 ₽ |
    | RAM (for 1 GB) | 0.0625 ₽ | 0.0750 ₽ |

- Platform Intel Cascade Lake:

    | Computing resources | Cost of 1 hour, without VAT | Cost of 1 hour, with VAT |
    | ----- | ----- | ----- |
    | 5%+ of vCPU | 0.0530 ₽ | 0.0636 ₽ |
    | 20%+ vCPU | 0,1590 ₽ | 0,1908 ₽ |
    | 50%+ vCPU | 0,2330 ₽ | 0,2796 ₽ |
    | 100% of vCPU | 0.1700 ₽ | 0.2040 ₽ |
    | RAM (for 1 GB) | 0.0410 ₽ | 0.0492 ₽ |

### Operating systems {#burstable-instance-os}

| OS | Cost per vCPU per hour,<br/> without VAT | Cost per vCPU per hour,<br/> with VAT |
| ----- | ----- | ----- |
| Linux for all core types | 0 ₽ | 0 ₽ |
| Windows Server for 5%+ of vCPU | 0.5288 ₽ | 0.6346 ₽ |
| Windows Server for 20%+, 50%+, 100% vCPU | 1.0576 ₽ | 1.2691 ₽ |

### Disks, snapshots, and images {#prices-storage}

| Type | Cost of 1 GB per month,<br/> without VAT | Cost of 1 GB per month,<br/> with VAT |
| ----- | ----- | ----- |
| Fast network drive (NVMe) | 6.2034 ₽ | 7.4441 ₽ |
| Standard disk drive (HDD) | 1.7373 ₽ | 2.0847 ₽ |
| Snapshot | 1.8559 ₽ | 2.2271 ₽ |
| Image | 1.8559 ₽ | 2.2271 ₽ |

### Outgoing traffic {#prices-traffic}

[!INCLUDE-NOTITLE [pricing-egress-traffic](../_includes/pricing/pricing-egress-traffic.md)]
