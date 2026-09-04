# Lab 02 — Hostname and Hosts Configuration: Commands and Purpose

## 1. Check the Current Hostname

```bash
hostname
```

### Why?

Checks the hostname assigned to the Ubuntu machine.

### Actual Output

```text
loki223
```

---

## 2. Check the Server IP Addresses

```bash
hostname -I
```

### Why?

Displays the IP addresses assigned to the machine.

### Actual Output

```text
10.0.2.15 192.168.56.101
```

The system also reported IPv6 addresses.

---

## 3. Configure Hostname-to-IP Mapping

The Puppet Server hostname was mapped in `/etc/hosts`:

```text
10.0.2.15 loki223.lpu.com
```

### Why?

This allows the machine to resolve the Puppet Server's hostname to its IP address without depending on an external DNS server.

---

## 4. Verify `/etc/hosts` Mapping

```bash
grep -E 'loki223\.lpu\.com|10\.0\.2\.15' /etc/hosts
```

### Why?

Checks whether the required Puppet Server hostname-to-IP mapping exists in `/etc/hosts`.

### Result

The mapping for `loki223.lpu.com` was configured.

---

## 5. Verify Hostname Resolution

```bash
getent hosts loki223.lpu.com
```

### Why?

Tests whether Linux can resolve `loki223.lpu.com` to an IP address.

### Result

The Puppet Server hostname resolved successfully.

---

## 6. Verify Puppet Server Name

```bash
sudo /opt/puppetlabs/bin/puppet config print server --section server
```

### Why?

Checks the Puppet configuration to confirm that Puppet is using the expected Puppet Server hostname.

### Actual Output

```text
loki223.lpu.com
```

---

# Configuration Relationship

```text
10.0.2.15
    ↓
loki223.lpu.com
    ↓
Puppet Server
    ↓
TCP 8140
```

## Result

The Ubuntu hostname, Puppet Server hostname, and hostname-to-IP mapping were configured and verified successfully.
