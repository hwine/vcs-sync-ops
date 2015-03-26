# -*- mode: ruby -*-
# vi: set ft=ruby sw=2 ts=2 et:

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # new boxen
  config.vm.box = "dummy-aws"
  config.vm.provider :aws do |aws, override|
    aws.instance_type = "t2.micro"
    aws.access_key_id = "AKIAICOOTZWNOPNXNSXQ"
    aws.secret_access_key = "sv++P36cs2L6c6ER6caLI399Ma4iMFrM0tzVyQgL"
    #aws.session_token = "SESSION TOKEN"
    aws.keypair_name = "hwine"
    aws.region = "us-west-2"

    aws.ami = "ami-29ebb519"
    aws.tags = {
      'Name' => 'hwine_test'
    }

    override.ssh.username = "ubuntu"
    override.ssh.private_key_path = "~/.ssh/hwine-moz-dev-services.pem"
  end

  config.vm.provider "docker" do |d|
    d.cmd     = ["/sbin/my_init", "--enable-insecure-key"]
    #d.image   = "phusion/baseimage"
    d.build_dir = "."
    d.has_ssh = true
    config.ssh.username = "root"
    config.ssh.insert_key = false
    config.ssh.private_key_path = "phusion.key"
    # Dockerfile contains any commands needed to get to same as AMI
  end
  config.vm.provider "virtualbox" do |d|
    d.vm.box = "ubuntu/trusty64"
  end
  config.vm.provision "shell",
      inline: "echo Hello, World"

  # provision using ansible 
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "onetime.yml"
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "vcs2vcs.yml"
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "legacy.yml"
  end

end
