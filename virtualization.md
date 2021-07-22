# Naming Things Is Hard - Virtualization Edition

- node - physical device
- machine - running container or vm.
- manager -
- engine - runs machines
- orchestrator - manages ha
- workload - multiple machines run as a whole e.g. kubernetes pod


- node
	- container orchestrator
	- container engine
		- container
	- vm engine
		- vm
			- container engine
				- ...

orchestrators/engines can run in either

- standalone
- high availability (HA) - can migrate machines between nodes

modes.

## storage types

- template
- disk
- snapshot

### templates

- iso
- disk image
- container

### disk

#### vm

- qcow2
- raw

#### container

### template

## vm engine (hypervisor)

- qemu
- kvm
- bhyve
- virtualbox
- vmware
- exsi

## vm middleware

libvirt - provides a standardised interface to vm engines

## container runtime

- runc
- crun

## container engine

- docker
- containerd
- podman
- kubernetes?

## container orchestration

- kubernetes
- swarm
- portainer
- docker-compose

## vm orchestration

- Vagrant
- virt-manager - single node?
- Proxmox -  KVM/LXC
- Multipass
- Metal-As-A-Service (MAAS)
- oVirt
- VirtualBox

## container creation

docker


## vm creation

- packer

## vm provisioning

- ansible

## vm control

- terraform

## node inventory


## secret management

ansible vault
hashicorp vault


## logical volume management

allows disk to only write used space not the full disk size


## workload
