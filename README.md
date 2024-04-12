[![CI](https://github.com/de-it-krachten/ansible-role-vmware/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-vmware/actions?query=workflow%3ACI)


# ansible-role-vmware

Manage VMWare resources like templates, vms etc



## Dependencies

#### Roles
None

#### Collections
- community.vmware

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 37
- Fedora 38

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Upload iso images to vcenter
vm_iso_upload: false

# Delete the VM before creating the image
vm_destroy: yes

# Create the VM before creating the image
vm_create: yes

# Convert vm into a template
vm_template: yes

# Startup
vm_startup: no

# Type of ISO file to use
vm_iso_type: 'autoinstall'

# Amount of VM deployment in parallel
vmware_parallel_deployments: 1

# vm_name: template-ubuntu2204
# vm_guest_id: ubuntu64Guest
vm_folder: /templates

vm_settings:
  guest_id: "{{ vm_guest_id }}"
  disk:
    - size_gb: 60
      type: thick
      autoselect_datastore: true
      # datastore: "{{ vm_datastore }}"
  cdrom: []
  # cdrom:
  #   - type: none
  #     controller_type: ide
  #      controller_number: 0
  #      unit_number: 0
  hardware:
    memory_mb: 2048
    num_cpus: 2
    boot_firmware: efi
    secure_boot: true
  networks:
    - connected: yes
      device_type: vmxnet3
      start_connected: yes
      type: static
      name: "{{ vm_vnet }}"
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'vmware'
  hosts: all
  become: 'yes'
  tasks:
    - name: No need to execute code without VMWare
      ansible.builtin.debug:
        msg: Nothing to do here
</pre></code>
