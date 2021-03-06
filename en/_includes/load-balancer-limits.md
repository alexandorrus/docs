#### Quotas {#quotas}

| Type of limit | Value |
| ----- | ----- |
| Number of load balancers per cloud | 2 |
| Number of target groups per cloud | 2 |

#### Limits {#limits}

| Type of limit | Value |
| ----- | ----- |
| Number of resources per target group | 254 |
| Number of listening ports | 10 |
| Number of health checks per attached target group | 1 |
| Status check protocol | TCP, HTTP |

#### Other restrictions {#other-restrictions}

A particular target group can only contain target resources from a single cloud network.

A target group can include resources that are connected to the same subnet within a single availability zone.

You can create a load balancer without a listener.

Target resources must accept connections on the same port as the listener does.

You cannot attach the same target resource to different load balancers.

Health checks are transmitted from the IP address range `198.18.235.0/24`.

Consider the number of simultaneous connections [limit](../vpc/concepts/limits.md) when attaching a target resource to the load balancer. 
