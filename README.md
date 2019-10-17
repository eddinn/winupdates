# winupdates

Ansible playbook/role to update Windows servers with Ansible via WinRM

---

## WinRM setup script

Use the `winrm-config.ps1` PowerShell script to configure WinRM on servers that don't have it installed or configured.
Make sure to adjust the script to your needs, usually the defaults are suficient.
FYI: The defaults use cert authentication to connect.

## The `hosts` file

4 hostsgroups and 1 vargroup are in the file:

* [winprod]
* [wintest]
* [windows:children] # Incorperates winprod and wintest into a combined windows group
* [winrmtest] # For testing purposes of winrm
* [winrmtest:vars] # Vars for testing purposes

## the `win-ping.yml` file

Basic test to see if you are able to connect with ansible to the server via WinRM

## The `roles` folder

This folder includes the winupdate role module.
You can customize it with vars, and edit the `tasks/main.yml` if needed.
The `main.yml` file contains the tasks/actions to be carried out by the role, and you need to update it to your needs if you want to disable rebooting, edit update severity categories and so on.
By default it installs Critical and Security updates, and reboots the machine if required.

> Note: Make sure to edit the vars accordingly to your setup if needed

### Handy links for reference

How to setup WinRM:
<https://www.ansible.com/blog/connecting-to-a-windows-host>

How to use Ansible Vault:
<https://serversforhackers.com/c/how-ansible-vault-works>
