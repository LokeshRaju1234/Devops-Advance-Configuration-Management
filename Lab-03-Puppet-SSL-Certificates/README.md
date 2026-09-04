# Lab 03 — Puppet SSL Certificates

## Objective

To understand and verify the SSL certificate infrastructure used by Puppet for secure communication between the Puppet Server and Puppet agents.

## Concepts Covered

* Puppet Certificate Authority (CA)
* Puppet SSL certificates
* Puppet certname
* Server certificate identity
* Certificate management
* SSL-based trust between Puppet nodes

## Puppet Certificate Authority

Puppet uses a Certificate Authority (CA) to issue and manage certificates for Puppet nodes.

The CA is responsible for establishing trust between the Puppet Server and agents.

## Puppet Server Identity

The Puppet Server in this environment uses:

```text
loki223.lpu.com
```

as its Puppet certificate identity (certname).

## Certificate Verification

The Puppet CA was checked using the Puppet Server CA command.

Certificates managed by the CA were successfully listed.

The certificate list was also filtered to verify entries associated with:

```text
loki223
loki223.lpu.com
```

## Why Certificates Are Required

Puppet agents communicate with the Puppet Server over HTTPS.

Certificates provide authentication and establish a trusted SSL/TLS connection between the Puppet Server and Puppet agents.

## Verification

The following were successfully verified:

* Puppet CA is available.
* Puppet certificates can be listed.
* The Puppet Server certificate identity is `loki223.lpu.com`.
* The Puppet Server is configured to use `loki223.lpu.com`.

## Result

The Puppet SSL and Certificate Authority configuration was successfully verified.
