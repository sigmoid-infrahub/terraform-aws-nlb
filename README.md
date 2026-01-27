# Module: NLB

This module creates and manages an AWS Network Load Balancer (NLB), including target groups and listeners.

## Features
- Create Network Load Balancer (Internal or External)
- Configure Listeners (TCP/UDP/TLS)
- Manage Target Groups
- Support for Access Logs
- High performance Layer 4 load balancing

## Usage
```hcl
module "nlb" {
  source = "../../terraform-modules/terraform-aws-nlb"

  name               = "my-nlb"
  load_balancer_type = "network"
  subnets            = ["subnet-12345678", "subnet-87654321"]
}
```

## Inputs
| Name | Type | Default | Description |
|------|------|---------|-------------|
| `name` | `string` | n/a | Load balancer name |
| `load_balancer_type` | `string` | n/a | Load balancer type |
| `internal` | `bool` | `false` | Internal load balancer |
| `subnets` | `list(string)` | n/a | Subnet IDs |
| `security_groups` | `list(string)` | `[]` | Security group IDs |
| `enable_deletion_protection` | `bool` | `false` | Enable deletion protection |
| `enable_cross_zone_load_balancing` | `bool` | `true` | Enable cross-zone load balancing |
| `access_logs` | `any` | `null` | Access log configuration |
| `listeners` | `any` | `[]` | Listeners configuration |
| `target_groups` | `any` | `[]` | Target groups configuration |
| `tags` | `map(string)` | `{}` | Tags to apply |

## Outputs
| Name | Description |
|------|-------------|
| `lb_arn` | Load balancer ARN |
| `dns_name` | Load balancer DNS name |
| `module` | Full module outputs |

## Environment Variables
None

## Notes
- Network Load Balancers are ideal for high-throughput, low-latency traffic.
- Unlike ALB, NLB operates at the transport layer (Layer 4).
