# Lab 01 — Puppet Server Setup: Commands and Purpose

## 1. Check Ubuntu Version

```bash
lsb_release -a
```

### Why?

Checks the operating system distribution, version, release, and codename.

### Actual Result

```text
Ubuntu 24.04.4 LTS
Release: 24.04
Codename: noble
```

---

## 2. Check Puppet Version

```bash
sudo /opt/puppetlabs/bin/puppet --version
```

### Why?

Checks the installed Puppet version.

### Actual Result

```text
8.21.0
```

---

## 3. Check Linux Hostname

```bash
hostname
```

### Why?

Checks the hostname of the Linux machine.

### Actual Result

```text
loki223
```

---

## 4. Check Puppet Server Service

```bash
sudo systemctl status puppetserver --no-pager
```

### Why?

Checks whether the Puppet Server systemd service is currently running.

### Result

Puppet Server was verified as running.

---

## 5. Check Puppet Server Port

```bash
sudo ss -lntp | grep 8140
```

### Why?

Checks whether a process is listening for network connections on Puppet Server's default port, TCP 8140.

### Actual Result

```text
LISTEN 0 50 *:8140 *:* users:(("java",pid=1295,fd=27))
```

### Result

Puppet Server is listening on port `8140`.

---

## 6. Test Puppet Server HTTPS API

```bash
curl -k https://loki223.lpu.com:8140/status/v1/simple
```

### Why?

Tests whether the Puppet Server HTTPS API is responding.

### Actual Result

```text
running
```

### Result

The Puppet Server HTTPS API is responding successfully.

---

## 7. Verify Hostname Resolution

```bash
getent hosts loki223.lpu.com
```

### Why?

Checks whether the Puppet Server hostname resolves to an IP address.

### Result

`loki223.lpu.com` was successfully resolved.

---

## 8. Check Puppet Server Configuration

```bash
sudo /opt/puppetlabs/bin/puppet config print server --section server
```

### Why?

Checks which Puppet Server hostname is configured in Puppet.

### Actual Result

```text
loki223.lpu.com
```

---

## 9. Check Puppet Configuration File

```bash
sudo cat /etc/puppetlabs/puppet/puppet.conf
```

### Why?

Displays the actual Puppet configuration file.

### Relevant Configuration

```ini
[server]
server = loki223.lpu.com
```

### Result

Puppet is configured to use `loki223.lpu.com` as the server.

---

## 10. Check Puppet CA Certificates

```bash
sudo /opt/puppetlabs/bin/puppetserver ca list --all
```

### Why?

Lists certificates managed by the Puppet Certificate Authority.

### Result

The Puppet CA successfully listed the certificates.

---

## 11. Check Server Certificate Entries

```bash
sudo /opt/puppetlabs/bin/puppetserver ca list --all | grep -E 'loki223|loki223.lpu.com'
```

### Why?

Filters the CA output to identify certificates associated with the Puppet Server.

### Result

Entries associated with `loki223` / `loki223.lpu.com` were found.

---

## 12. Check Puppet Certname

```bash
sudo /opt/puppetlabs/bin/puppet config print certname
```

### Why?

Checks the certificate identity Puppet uses for this node.

### Actual Result

```text
loki223.lpu.com
```

---

## 13. Check Puppet Server Process

```bash
ps aux | grep '[p]uppetserver'
```

### Why?

Checks for the running Puppet Server process.

### Result

The Puppet Server process was verified.

---

## 14. Check Automatic Startup

```bash
sudo systemctl is-enabled puppetserver
```

### Why?

Checks whether Puppet Server is configured to start automatically when Ubuntu boots.

### Actual Result

```text
enabled
```

---

## 15. Check Server IP Addresses

```bash
hostname -I
```

### Why?

Displays the IP addresses assigned to the Linux machine.

### Actual Result

```text
10.0.2.15 192.168.56.101
```

The system also reported IPv6 addresses.

---

## 16. Check Puppet Executable Location

```bash
which puppet
```

### Why?

Checks where the Puppet executable is installed and helps explain why the full Puppet Labs path is used with `sudo`.

The full Puppet executable path used throughout the practical is:

```text
/opt/puppetlabs/bin/puppet
```

---

# Lab 01 Summary

The Puppet Server environment was checked and verified through service, network, HTTPS, hostname, configuration, certificate, and process checks.

## Important Server Details

```text
Hostname:       loki223
Certname:       loki223.lpu.com
Puppet Version: 8.21.0
Puppet Port:    8140
OS:             Ubuntu 24.04.4 LTS
Codename:       noble
```

## Result

Puppet Server was successfully configured and verified.
