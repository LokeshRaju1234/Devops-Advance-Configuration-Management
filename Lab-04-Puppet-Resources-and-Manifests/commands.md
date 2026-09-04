# Lab 04 — Puppet Resources and Manifests: Commands and Purpose

## 1. Create a Puppet Manifest

Example manifest:

```puppet
file { '/tmp/puppet-test.txt':
  ensure  => file,
  content => 'Managed by Puppet',
}
```

### Why?

Defines a Puppet `file` resource and describes its desired state.

---

## 2. Apply a Puppet Manifest

```bash
sudo /opt/puppetlabs/bin/puppet apply manifest.pp
```

### Why?

Compiles and applies the Puppet manifest to the local system.

### Result

Puppet successfully compiled and applied the catalog.

---

## 3. Run Puppet in Noop Mode

```bash
sudo /opt/puppetlabs/bin/puppet apply --noop manifest.pp
```

### Why?

Simulates the Puppet run without making actual changes.

This is useful for safely previewing configuration changes.

### Result

Puppet compiled the catalog and displayed the changes that would be made without applying them.

---

## 4. Check a Managed File

```bash
ls -l /tmp/puppet-test.txt
```

### Why?

Verifies that the file resource exists on the system.

---

## 5. Display the Managed File

```bash
cat /tmp/puppet-test.txt
```

### Why?

Verifies the content managed by Puppet.

---

# Important Puppet Concepts

## Resource

A resource represents a system component that Puppet can manage.

Example:

```puppet
file { '/tmp/example.txt':
  ensure => file,
}
```

## Attribute

An attribute describes the desired state of a resource.

Examples:

```text
ensure
content
owner
group
mode
```

## Manifest

A manifest contains Puppet resources and describes the desired configuration.

## Catalog

Puppet compiles manifests into a catalog containing the resources and relationships that should be applied.

## Declarative Configuration

Puppet describes the desired end state rather than providing imperative instructions for how to reach that state.

## Idempotency

Applying the same Puppet configuration repeatedly should leave an already-correct system unchanged.

## Result

Puppet resources, manifests, `puppet apply`, noop mode, catalogs, declarative configuration, and idempotency were documented and practiced.
