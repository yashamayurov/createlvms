Role Name
=========

createlvms

Роль используется создания logical volume для использования их как iSCSI-target в роли ondrejhome.targetcli

Requirements
------------

Centos7

Role Variables
--------------

```yaml
iscsi_physical_device: sdb      # Физичекий диск
iscsi_part_number: 1            # Номер раздела на диске         
iscsi_partition_path: "/dev/{{ iscsi_physical_device }}{{ iscsi_part_number }}"   # Путь к разделу, где создаются lvm

iscsi_volumegroup_name: iscsi

iscsi_lvol_list:
  - { name: lvAriadna, size: 500G, path: "/dev/{{ iscsi_volumegroup_name }}/lvAriadna", type: 'block', initiator: iqn.1991-05.com.microsoft:ariadna-db.mood51.loc }
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```yaml
  roles: 
  - { role: createlvms }
  - { role: ondrejhome.targetcli }
```

Author Information
------------------

Iakov Maiurov
