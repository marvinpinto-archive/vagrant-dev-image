require 'yaml'

# Load the user-specific yaml file
vconfig = YAML::load_file("vagrant_config.yaml")

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Every Vagrant virtual environment requires a box to build off of
  config.vm.box = vconfig['box_name']

  # Hostname is relevant to which puppet manifest gets applied
  config.vm.hostname = vconfig['hostname']

  # Share the public and private puppet manifest directories
  config.vm.synced_folder vconfig['puppet_public_repo_dir'], "/usr/local/etc/puppet-public"
  config.vm.synced_folder vconfig['puppet_private_repo_dir'], "/usr/local/etc/puppet-private"

  # Install the latest available version of puppet
  config.vm.provision "shell", path: "scripts/install_puppet.sh"

end
