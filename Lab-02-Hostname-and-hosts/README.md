# Lab 02 — Puppet Hostname and Hosts Configuration

## Objective

To configure and verify the hostname and hostname resolution required for Puppet Server communication.

## Environment

| Component          | Details            |
| ------------------ | ------------------ |
| Operating System   | Ubuntu 24.04.4 LTS |
| Hostname           | `loki223`          |
| Puppet Server FQDN | `loki223.lpu.com`  |
| Puppet Server IP   | `10.0.2.15`        |

## Concepts Covered

* Linux hostname
* Fully Qualified Domain Name (FQDN)
* `/etc/hosts`
* Hostname-to-IP mapping
* Puppet Server name resolution

## Configuration

The Puppet Server is identified as:

```text
loki223.lpu.com
```

The hostname was mapped to the server IP through `/etc/hosts`:

```text
10.0.2.15 loki223.lpu.com
```

## Why This Configuration Is Required

Puppet agents need to know the hostname of the Puppet Server so they can establish communication with it.

The hostname:

```text
loki223.lpu.com
```

must resolve to the correct server IP address.

## Verification

Hostname and name resolution were verified successfully.

The Puppet Server hostname resolved correctly to its configured IP address.

## Result

The Puppet Server hostname and hostname-to-IP mapping were successfully configured and verified.
