---
tags:
  - tryhackme/rooms
date-created: 2025-02-18
originalUrl: https://tryhackme.com/room/onpremisesiac
---
# THM Room | On-Premises IaC
*IaC → Infrastructure as Code*

On-Prem IaC == high effort, high control, high responsibility

## Vagrant
| Term        | Definition                                                                                                                                                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Provider    | A Vagrant provider is the virtualisation technology that will be used to provision the IaC deployment. Vagrant can use different providers such as Docker, VirtualBox, VMware, and even AWS for cloud-based deployments. |
| Provision   | Provision is the term used to perform an action using Vagrant. This can be actions such as adding new files or running a script to configure the host created with Vagrant.                                              |
| Configure   | Configure is used to perform configuration changes using Vagrant. This can be changed by adding a network interface to a host or changing its hostname.                                                                  |
| Variable    | A variable stores some value that will be used in the Vagrant deployment script.                                                                                                                                         |
| Box         | The Box refers to the image that will be provisioned by Vagrant.                                                                                                                                                         |
| Vagrantfile | The Vagrantfile is the provisioning file that will be read and executed by Vagrant.                                                                                                                                      |

## Ansible
| Term     | Definition                                                                                                                                                                                                                                                                                                                                                                                                                               |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Playbook | An Ansible playbook is a YAML file with a series of steps that will be executed.                                                                                                                                                                                                                                                                                                                                                         |
| Template | Ansible allows for the creation of template files. These act as your base files, like a configuration file, with placeholders for Ansible variables, which will then be injected into at runtime to create a final file that can be deployed to the host. Using Ansible variables means that you can change the value of the variable in a single location and it will then propagate through to all placeholders in your configuration. |
| Role     | Ansible allows for the creation of a collection of templates and instructions that are then called roles. A host that will be provisioned can then be assigned one or more of these roles, executing the entire template for the host. This allows you to reuse the role definition with a single line of configuration where you specify that the role must be provisioned on a host.                                                   |
| Variable | A variable stores some value that will be used in the Ansible deployment script. Ansible can take this a step further by having variable files where each file has different values for the same variables, and the decision is then made at runtime for which variable file will be used.                                                                                                                                               |


## Differences Between Vagrant and Ansible

| **Feature/Aspect**               | **Vagrant**                                                         | **Ansible**                                                               |
| -------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| **Configuration Language**       | Ruby (for Vagrantfiles).                                            | YAML (for Playbooks).                                                     |
| **Integration with Other Tools** | Often used with provisioning tools like Chef, Puppet, or Ansible.   | Can be used standalone or integrated with other CI/CD tools.              |
| **Complexity**                   | Relatively straightforward for setting up development environments. | Higher complexity for larger infrastructures and advanced configurations. |
| **Scalability**                  | More suited for smaller-scale, individual development environments. | Highly scalable, suitable for managing complex, multi-tier applications.  |
| **Execution Model**              | Procedural style with sequential execution steps.                   | Declarative model, describing the desired state of the system.            |


## Security Concerns in On-Prem IaC

Links
- [OWASP IaC Cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/Infrastructure_as_Code_Security_Cheat_Sheet.html)
- [NIST SP 800-204C](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-204C.pdf) has some IaC guidance

"...In total, there are four main elements to consider."
1. Dependencies
2. Defaults
3. Insufficient Hardening
4. Remote Code Execution as a Feature




# Task 7 - Attacking On-Prem IaC

- This task is also good for getting practice with **SSH proxying**...