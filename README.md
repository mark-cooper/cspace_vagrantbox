cspace_vagrantbox
=================

Create a CollectionSpace server using vagrant and the one-click-installer with a single command.

Requirements
------------

_Software_

- [Virtualbox](https://www.virtualbox.org)
- [Vagrant](https://www.vagrantup.com)

After installing vagrant run:

```
vagrant plugin install vagrant-vbguest
```

_Hardware_

A CPU that supports virtualization and 4GB RAM for the VM.

Installation
------------

Download the repository then:

```
vagrant up
```

**This will take a while to complete ... grab some coffee and read a book.**

To access the server:

```
vagrant ssh
```

To complete the installation follow the instructions from the "After installation" section of the [CollectionSpace wiki](http://wiki.collectionspace.org/display/DOC/Automated+installer+for+CollectionSpace+4.1).

To access CollectionSpace in the browser:

```
# port forwarded address
http://localhost:8180/collectionspace/ui/core/html/

# or via the ip address of the vagrant box
http://10.11.12.45:8180/collectionspace/ui/core/html/
```

Starting over
-------------

```
vagrant destroy
vagrant up
```

Troubleshooting
---------------

**Error: "A customization command failed"**

Windows issue. Replace:

```
v.customize ["modifyvm", :id, "--cpus", `awk "/^processor/ {++n} END {print n}" /proc/cpuinfo 2> /dev/null || sh -c 'sysctl hw.logicalcpu 2> /dev/null || echo ": 2"' | awk \'{print \$2}\' `.chomp ]
```

With:

```
v.customize ["modifyvm", :id, "--cpus", 2 ]
```

Where `2` should equal the number of cpu cores available.

**Error: "executable 'bdstar' vagrant is trying to run ...**

This is an upgrade issue on Windows. Uninstall and reinstall vagrant.

**Error: "invalid byte sequence in US-ASCII"**

Not sure what provokes this. Follow the starting over steps.

**Error: "out of memory"**

If provisioning fails during the build phase re-run it:

```
vagrant provision
```

**Error: "the guest machine entered an invalid state"**

Ensure VT-x is enabled.

---
