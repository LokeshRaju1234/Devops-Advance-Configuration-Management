# Lab 03 — Puppet SSL Certificates: Commands and Purpose

## 1. List Puppet CA Certificates

```bash
sudo /opt/puppetlabs/bin/puppetserver ca list --all
```

### Why?

Lists the certificates managed by the Puppet Certificate Authority (CA).

### Result

The Puppet CA successfully listed the certificates.

---

## 2. Filter the Certificate List for the Puppet Server

```bash
sudo /opt/puppetlabs/bin/puppetserver ca list --all | grep -E 'loki223|loki223.lpu.com'
```

### Why?

Filters the certificate list to identify certificate entries associated with the Puppet Server.

### Result

Entries associated with `loki223` / `loki223.lpu.com` were found.

---

## 3. Check the Puppet Certname

```bash
sudo /opt/puppetlabs/bin/puppet config print certname
```

### Why?

Checks the certificate identity used by the Puppet node.

### Actual Output

```text
loki223.lpu.com
```

---

## 4. Check the Configured Puppet Server

```bash
sudo /opt/puppetlabs/bin/puppet config print server --section server
```

### Why?

Verifies which Puppet Server hostname is configured for the server.

### Actual Output

```text
loki223.lpu.com
```

---

## 5. Check the Puppet Configuration File

```bash
sudo cat /etc/puppetlabs/puppet/puppet.conf
```

### Why?

Displays the Puppet configuration and verifies the configured server name.

### Relevant Configuration

```ini
[server]
server = loki223.lpu.com
```

---

# SSL Communication Concept

Puppet uses SSL/TLS certificates to establish trusted communication between the Puppet Server and Puppet agents.

The basic relationship is:

```text
Puppet Server
    |
    | Certificate Authority (CA)
    |
    +---- Server Certificate
    |
    +---- Agent Certificates
```

The Puppet CA manages certificates and establishes trust between Puppet nodes.

## Server Identity

```text
Certname: loki223.lpu.com
```

## Result

The Puppet Certificate Authority, certificate identities, Puppet certname, and configured Puppet Server were successfully verified.
