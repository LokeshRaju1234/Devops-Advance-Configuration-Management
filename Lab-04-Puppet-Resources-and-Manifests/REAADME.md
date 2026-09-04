# Lab 04 — Puppet Resources and Manifests

## Objective

To understand Puppet resources and manifests and use Puppet to declaratively manage system configuration.

## Concepts Covered

* Puppet manifests
* Puppet resources
* Resource types
* Resource attributes
* Declarative configuration
* Puppet catalog
* `puppet apply`
* Puppet noop mode

## Puppet Manifest

A Puppet manifest is a file containing Puppet code that describes the desired state of a system.

Example:

```puppet
file { '/tmp/puppet-test.txt':
  ensure  => file,
  content => 'Managed by Puppet',
}
```

The manifest describes what the system should look like rather than providing a sequence of commands to execute.

## Puppet Resources

Puppet manages system configuration through resources.

Common resource types include:

* `file`
* `package`
* `service`
* `user`
* `group`
* `exec`

Each resource contains attributes that describe its desired state.

## Puppet Apply

A manifest can be applied locally using:

```bash
sudo /opt/puppetlabs/bin/puppet apply manifest.pp
```

Puppet compiles the manifest into a catalog and applies the desired configuration.

## Noop Mode

Puppet can preview changes without actually applying them:

```bash
sudo /opt/puppetlabs/bin/puppet apply --noop manifest.pp
```

Noop mode is useful for safely checking what Puppet would change.

## Idempotency

Puppet is designed to be idempotent.

If the system already matches the desired state, running the same manifest again should not make unnecessary changes.

## Result

Puppet resources and manifests were successfully studied and used to declaratively manage system configuration.
