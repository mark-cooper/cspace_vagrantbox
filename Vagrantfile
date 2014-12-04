# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "cspace" do |app|
    app.vm.hostname = "cspace"
    app.vm.box = "ubuntu/trusty64"

    app.vm.network :private_network, ip: "10.11.12.45"
    app.vm.network :forwarded_port, guest: 8180, host: 8180

    app.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--memory", 2048]
      if not RUBY_PLATFORM.downcase.include?("mswin")
        v.customize ["modifyvm", :id, "--cpus", `awk "/^processor/ {++n} END {print n}" /proc/cpuinfo 2> /dev/null || sh -c 'sysctl hw.logicalcpu 2> /dev/null || echo ": 2"' | awk \'{print \$2}\' `.chomp ]
      end
    end
  end

  config.vm.provision :shell, path: 'https://raw.github.com/cspace-puppet/cspace_puppet_bootstrap/master/scripts/bootstrap-cspace-modules.sh', args: "-y"

end
