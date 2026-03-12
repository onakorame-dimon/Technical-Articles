# Ansible

![](../.gitbook/assets/ansilbe_logo.png)

## What is Ansible

Ansible is a configuration management and automation tool that uses uses simple, human-readable scripts called playbooks to define the desired state of managed systems.

There are various configuration management tools available. Some of these include: [Chef](https://www.chef.io/) and [Puppet](https://www.puppet.com/).

However, what makes Ansible stand out is because it is "agentless" this means that it does not require the installation of an "agent" (additional software) on the devices it manages.

It uses remote connections via SSH (on Unix/Linux based systems) or Windows Remote Management (WinRm) on Windows devices.

## Why use Ansible

Suppose you are a system administrator responsible for management of multiple devices across multiple platforms how do you maintain these systems, or push software updates on all these systems?

You can write a custom script on the machines to accomplish this, however, individual management can introduce config drift and errors.

Also, this method is not scalable. For instance, imagine you are responsible for responsible for managing hundreds of servers in an enterprise environment, writting scripts to manage such large number of devices would not be feasible and is prone to introduce errors.

Here's where Ansible comes in.

## Ansible Architecture

![Ansible Architecture](../.gitbook/assets/ansible-architecture.png)

**Control Node**

A system on which Ansible is installed, and ansible commands are run to configure **managed nodes.**

**Managed Node**

A remote system, or host, that Ansible controls.

## Basic Terminologies

### Playbooks

Contains instruction, scripts, executed by Ansible, to run configurations on remote systems (Nodes). Playbooks are written on the control node, and it is written in [YAML syntax](https://docs.ansible.com/projects/ansible/latest/reference_appendices/YAMLSyntax.html).

A playbook consists of one or more "plays" in an ordered list. Each paly executes part of the overall goal of the playbook

Each play consists of **tasks** to execute (which are executed from top to bottom) And the managed node to target.

### Tasks

A task is an action to be applied on a managed host. This could be: Executing a command, Running a script, or Installing a software package

### Modules

Modules are the programs Ansible uses to perform actions on managed hosts. Each task in a playbook calls a module to carry out a specific operation such as installing packages, managing users, copying files, or controlling services.

Most Ansible modules are written so that they are **idempotent.** This means that even if an operation is repeated multiple times it will always place the system into the same state.

### Directives

Directives are YAML keywords that control how Ansible interprets and runs a playbook. They describe how tasks should run, while modules perform the actual work.

### Ansible Roles

Roles are a standardized way of organizing and reusing Ansible automation. A role groups related tasks, variables, and files so that it can be reused across multiple playbooks.

### Ansible Inventory

The inventory defines the hosts that Ansible manages.

It lists contains the managed devices, and it allows you to organize them into groups, which let playbooks to target specific machines based on the group they belong.

## Example Inventory

**Ansible Inventory**

The Ansible inventory can be writen in [YAML](https://en.wikipedia.org/wiki/YAML) or [INI](https://en.wikipedia.org/wiki/INI_file) format

**Inventory file in INI format**

```ini
[webservers]
web1 ansible_host=192.168.56.10
web2 ansible_host=192.168.56.11

[dbservers]
db1 ansible_host=192.168.56.20
```

In the above configuration, **\[webservers]** and **\[dbservers]** are groups. Hosts placed under them belong to that group

**Inventory file in YAML format**

```yaml

all:
  children:
    webservers:
      hosts:
        web1:
          ansible_host: 192.168.56.10
        web2:
          ansible_host: 192.168.56.11

    dbservers:
      hosts:
        db1:
          ansible_host: 192.168.56.20
```

In the preceeding YAML file **all** is the root group, **children** defines subgroups. **hosts** lists the machines in each group

## Playbook Illustrated

**Ansible Playbook**

The below Image shows the contents of a playbook used to automate the creation of users on a Linux system

![Ansible Playbook](../.gitbook/assets/playbook.png)

## Further Learning

This article is meant to be a bird's eye view of Ansible and its typical usage.

For a more detailed course on Ansible, check out this video series: [Ansible 101 with Jeff Geerling](https://www.youtube.com/playlist?list=PL2_OBreMn7FqZkvMYt6ATmgC0KAGGJNAN)

And for hands on practice, get you hands dirty by trying out these labs: [Ansible Labs](../ansible-labs/)

**Stay Passionate !** :smiley: :sparkles: :sparkles:
