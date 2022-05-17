# Automated Pi-hole installation via ansible

## Requirements

* ssh access to the host machine from you local system

## Checks

* ansible-playbook main.yml --syntax-check
* ansible-lint

## Run tests

* Run: `molecule test`

## Setup

* Make copies of the following files and customize them to your liking:
  * `example.inventory.yml` to `inventory.yml` (replace IP address with your Pi's IP and set the correct ssh user).
  * `host_vars/example.raspberry.yml` to `host_vars/raspberry.yml` (do not forget to change the Pi-hole admin password)
* Run the playbook: `ansible-playbook main.yml`

The Pi-hole installation can be configured inside `templates/setupVars.conf.j2`.
* DNS Server is per default set to 1.1.1.1 Cloudflare (DNSSEC)
* The password can be configured within `host_vars/raspberry.yml`

## Upgrade Pi-hole version

1. Check https://github.com/pi-hole/pi-hole/releases for the latest version
2. Change `pihole_tag` inside `group_vars/all.yml`to the new tag
3. Run: `ansible-playbook  main.yml --tags upgrade`
