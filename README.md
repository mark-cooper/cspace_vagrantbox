cspace_vagrantbox
=================

Create a CollectionSpace server using vagrant and the one-click-installer with a single command.

Requirements
------------

- [Virtualbox](https://www.virtualbox.org)
- [Vagrant](https://www.vagrantup.com)

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

To the complete the installation follow the instruction from the "After installation" section of the [CollectionSpace wiki](http://wiki.collectionspace.org/display/DOC/Automated+installer+for+CollectionSpace+4.1).

To access CollectionSpace in the browser:

```
# port forwarded address
http://localhost:8180/collectionspace/ui/core/html/

# or via the ip address of the vagrant box
http://10.11.12.45:8180/collectionspace/ui/core/html/
```

Troubleshooting
---------------

**vagrant up - error "the guest machine entered an invalid state"**

Ensure VT-x is enabled.

---
