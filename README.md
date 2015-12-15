## Vagrant Dev Image

![unmaintained](http://img.shields.io/badge/status-unmaintained-red.png)

This is a basic dev image I spin up to test puppet manifest changes locally.
The `/usr/local/etc/puppet-public` and `/usr/local/etc/puppet-private`
directories are linked to the checked-out repos on my host machine.

Download the trusty64 box, if needed:
```bash
$ vagrant box add trusty64 https://vagrantcloud.com/ubuntu/boxes/trusty64/versions/1/providers/virtualbox.box
```

Clone this repo somewhere:
```bash
$ git clone https://github.com/marvinpinto/vagrant-dev-image.git vagrant-dev-image
```

Create a `vagrant_config.yaml` file inside the `vagrant-dev-image` directory
with appropriate values, for example:
```yaml
---
box_name: 'trusty64'
hostname: 'vagrant-test-hostname.example.org'
puppet_private_repo_dir: '~/src/my-puppet-private'
puppet_public_repo_dir: '~/src/my-puppet-private'
```

Bring up your brand new vagrant dev image:
```bash
$ cd vagrant-dev-image
$ vagrant up
$ vagrant ssh
```

To run puppet **inside** the vagrant image:
```bash
$ sudo /vagrant/scripts/puprun -y
```

Enjoy!
