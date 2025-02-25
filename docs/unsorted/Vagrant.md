# Vagrant
> **Sources used:**
> - tryhackme room | On-Premises IaC: https://tryhackme.com/room/onpremisesiac

## Links

### Related:
- [On-Premises IaC](../security%20writeups/tryhackme/rooms/On-Premises%20IaC.md)
- [Ansible](Ansible.md)

### Projects using vagrant:
- [Tabletop Lab Creation](https://github.com/MWR-CyberSec/tabletop-lab-creation) "...is a toolset for building a network of Active Directory hosts using Vagrant..."
- [Game of Active Directory](https://orange-cyberdefense.github.io/GOAD/) (GOAD) "...is a pentest active directory LAB project. The purpose of this lab is to give pentesters a vulnerable Active directory environment ready to use to practice usual attack techniques..."

## Key Points
*(Table is from tryhackme. See [On-Premises IaC](../security%20writeups/tryhackme/rooms/On-Premises%20IaC.md))*

| Term        | Definition                                                                                                                                                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Provider    | A Vagrant provider is the virtualisation technology that will be used to provision the IaC deployment. Vagrant can use different providers such as Docker, VirtualBox, VMware, and even AWS for cloud-based deployments. |
| Provision   | Provision is the term used to perform an action using Vagrant. This can be actions such as adding new files or running a script to configure the host created with Vagrant.                                              |
| Configure   | Configure is used to perform configuration changes using Vagrant. This can be changed by adding a network interface to a host or changing its hostname.                                                                  |
| Variable    | A variable stores some value that will be used in the Vagrant deployment script.                                                                                                                                         |
| Box         | The Box refers to the image that will be provisioned by Vagrant.                                                                                                                                                         |
| Vagrantfile | The Vagrantfile is the provisioning file that will be read and executed by Vagrant.                                                                                                                                      |

- **Vagrantfiles** are written in [Ruby](Ruby.md).
- IP ranges that are safe to use for local deployments:
	- 

## Ansible Integration
Vagrant is often combined with [Ansible](Ansible.md), using Vagrant's own **Ansible Provisioner**:

```ruby
config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provision/playbook.yml"
    ansible.become = true
end
```



## `vagrant` command

- Use `vagrant init <target box>` to generate a new *Vagrantfile*.


- `vagrant ssh` → Convenient ssh into your new environment that uses pre-configured SSH keys made during the pipeline's execution.

- `vagrant up` → Turn on your configured environment. This executes steps defined in the Vagrantfile of the current working directory.
	- If the **box** (VM image) used is sourced remotely, a copy will be downloaded for use across all Vagrantfiles configured for it.
- `vagrant suspend` → It's suspend.
- `vagrant resume` → Resume from suspended state.
- `vagrant halt` → It's shutdown.
- `vagrant destroy` → Completely delete the current environment/machine

### Provisioning Commands
- re-provisioning
	- 

## Tips when writing provisioning scripts
- Make your scripts are [idempotent](../terminology/idempotent.md). If ran more than once, the state of your environment should be the same as if you'd ran it only once.

[Vagrant - Creating Boxes](Vagrant%20-%20Creating%20Boxes.md)
