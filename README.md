Задание 


Ниже приведен вывод terraform apply
Который создает в облаке 3 вм
С помощью cloud-init задаются нужные параметры и устанавливаются нужные пакеты
Запуск playbook происходит после завершения работы cloud-init 
```
sypchik@Mirror:/mnt/c/Users/Sypchik/Desktop/home work/ansible/mnt-homeworks/08-ansible-03-yandex$ terraform apply --auto-approve
data.template_file.cloudinit: Reading...
data.template_file.cloudinit: Read complete after 0s [id=7c6c9700c5e1cfd0338370ffec84d3d803e3e522b277ab3ff5149fcefaf9feec]
data.yandex_compute_image.my_image: Reading...
data.yandex_compute_image.my_image: Read complete after 1s [id=fd8olkifs7mt71h2f6r9]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following
symbols:
  + create

Terraform will perform the following actions:

  # local_file.ansible_inventory will be created
  + resource "local_file" "ansible_inventory" {
      + content              = (known after apply)
      + content_base64sha256 = (known after apply)
      + content_base64sha512 = (known after apply)
      + content_md5          = (known after apply)
      + content_sha1         = (known after apply)
      + content_sha256       = (known after apply)
      + content_sha512       = (known after apply)
      + directory_permission = "0777"
      + file_permission      = "0777"
      + filename             = "./ansible/inventory/hosts.yaml"
      + id                   = (known after apply)
    }

  # null_resource.ansible_apply will be created
  + resource "null_resource" "ansible_apply" {
      + id = (known after apply)
    }

  # null_resource.wait_for_cloud_init["clickhouse"] will be created
  + resource "null_resource" "wait_for_cloud_init" {
      + id = (known after apply)
    }

  # null_resource.wait_for_cloud_init["lighthouse"] will be created
  + resource "null_resource" "wait_for_cloud_init" {
      + id = (known after apply)
    }

  # null_resource.wait_for_cloud_init["vector"] will be created
  + resource "null_resource" "wait_for_cloud_init" {
      + id = (known after apply)
    }

  # yandex_compute_instance.vm["clickhouse"] will be created
  + resource "yandex_compute_instance" "vm" {
      + created_at                = (known after apply)
      + folder_id                 = (known after apply)
      + fqdn                      = (known after apply)
      + gpu_cluster_id            = (known after apply)
      + hardware_generation       = (known after apply)
      + hostname                  = "clickhouse"
      + id                        = (known after apply)
      + maintenance_grace_period  = (known after apply)
      + maintenance_policy        = (known after apply)
      + metadata                  = {
          + "serial-port-enable" = "1"
          + "user-data"          = <<-EOT
                #cloud-config
                users:
                  - name: ubuntu
                    shell: /bin/bash
                    sudo: ["ALL=(ALL) NOPASSWD:ALL"]
                    ssh_authorized_keys:
                      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCW8VRL8= sypchik@Mirror
                package_update: true
                package_upgrade: true
                packages:
                  - libsoup2.4-1
                  - libappstream4
                  - python3
                  - python3-pip
                  - curl
                  - net-tools
                  - ca-certificates
                  - apt-transport-https
                  - gnupg
            EOT
        }
      + name                      = "ch-hw"
      + network_acceleration_type = "standard"
      + platform_id               = "standard-v3"
      + service_account_id        = (known after apply)
      + status                    = (known after apply)
      + zone                      = "ru-central1-a"

      + boot_disk {
          + auto_delete = true
          + device_name = (known after apply)
          + disk_id     = (known after apply)
          + mode        = (known after apply)

          + initialize_params {
              + block_size  = (known after apply)
              + description = (known after apply)
              + image_id    = "fd8olkifs7mt71h2f6r9"
              + name        = (known after apply)
              + size        = 10
              + snapshot_id = (known after apply)
              + type        = "network-hdd"
            }
        }

      + metadata_options (known after apply)

      + network_interface {
          + index              = (known after apply)
          + ip_address         = (known after apply)
          + ipv4               = true
          + ipv6               = (known after apply)
          + ipv6_address       = (known after apply)
          + mac_address        = (known after apply)
          + nat                = true
          + nat_ip_address     = (known after apply)
          + nat_ip_version     = (known after apply)
          + security_group_ids = (known after apply)
          + subnet_id          = (known after apply)
        }

      + placement_policy (known after apply)

      + resources {
          + core_fraction = 50
          + cores         = 2
          + memory        = 2
        }

      + scheduling_policy (known after apply)
    }

  # yandex_compute_instance.vm["lighthouse"] will be created
  + resource "yandex_compute_instance" "vm" {
      + created_at                = (known after apply)
      + folder_id                 = (known after apply)
      + fqdn                      = (known after apply)
      + gpu_cluster_id            = (known after apply)
      + hardware_generation       = (known after apply)
      + hostname                  = "lighthouse"
      + id                        = (known after apply)
      + maintenance_grace_period  = (known after apply)
      + maintenance_policy        = (known after apply)
      + metadata                  = {
          + "serial-port-enable" = "1"
          + "user-data"          = <<-EOT
                #cloud-config
                users:
                  - name: ubuntu
                    shell: /bin/bash
                    sudo: ["ALL=(ALL) NOPASSWD:ALL"]
                    ssh_authorized_keys:
                      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCW8VMQj1Ytwl2DVRv8/L8= sypchik@Mirror
                package_update: true
                package_upgrade: true
                packages:
                  - libsoup2.4-1
                  - libappstream4
                  - python3
                  - python3-pip
                  - curl
                  - net-tools
                  - ca-certificates
                  - apt-transport-https
                  - gnupg
            EOT
        }
      + name                      = "lh-hw"
      + network_acceleration_type = "standard"
      + platform_id               = "standard-v3"
      + service_account_id        = (known after apply)
      + status                    = (known after apply)
      + zone                      = "ru-central1-a"

      + boot_disk {
          + auto_delete = true
          + device_name = (known after apply)
          + disk_id     = (known after apply)
          + mode        = (known after apply)

          + initialize_params {
              + block_size  = (known after apply)
              + description = (known after apply)
              + image_id    = "fd8olkifs7mt71h2f6r9"
              + name        = (known after apply)
              + size        = 10
              + snapshot_id = (known after apply)
              + type        = "network-ssd"
            }
        }

      + metadata_options (known after apply)

      + network_interface {
          + index              = (known after apply)
          + ip_address         = (known after apply)
          + ipv4               = true
          + ipv6               = (known after apply)
          + ipv6_address       = (known after apply)
          + mac_address        = (known after apply)
          + nat                = true
          + nat_ip_address     = (known after apply)
          + nat_ip_version     = (known after apply)
          + security_group_ids = (known after apply)
          + subnet_id          = (known after apply)
        }

      + placement_policy (known after apply)

      + resources {
          + core_fraction = 50
          + cores         = 2
          + memory        = 2
        }

      + scheduling_policy (known after apply)
    }

  # yandex_compute_instance.vm["vector"] will be created
  + resource "yandex_compute_instance" "vm" {
      + created_at                = (known after apply)
      + folder_id                 = (known after apply)
      + fqdn                      = (known after apply)
      + gpu_cluster_id            = (known after apply)
      + hardware_generation       = (known after apply)
      + hostname                  = "vector"
      + id                        = (known after apply)
      + maintenance_grace_period  = (known after apply)
      + maintenance_policy        = (known after apply)
      + metadata                  = {
          + "serial-port-enable" = "1"
          + "user-data"          = <<-EOT
                #cloud-config
                users:
                  - name: ubuntu
                    shell: /bin/bash
                    sudo: ["ALL=(ALL) NOPASSWD:ALL"]
                    ssh_authorized_keys:
                      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCW8VPajVAede7d2Vj0IppI5Z2oG9BK4vxJXRL8= sypchik@Mirror
                package_update: true
                package_upgrade: true
                packages:
                  - libsoup2.4-1
                  - libappstream4
                  - python3
                  - python3-pip
                  - curl
                  - net-tools
                  - ca-certificates
                  - apt-transport-https
                  - gnupg
            EOT
        }
      + name                      = "vector-hw"
      + network_acceleration_type = "standard"
      + platform_id               = "standard-v3"
      + service_account_id        = (known after apply)
      + status                    = (known after apply)
      + zone                      = "ru-central1-a"

      + boot_disk {
          + auto_delete = true
          + device_name = (known after apply)
          + disk_id     = (known after apply)
          + mode        = (known after apply)

          + initialize_params {
              + block_size  = (known after apply)
              + description = (known after apply)
              + image_id    = "fd8olkifs7mt71h2f6r9"
              + name        = (known after apply)
              + size        = 10
              + snapshot_id = (known after apply)
              + type        = "network-ssd"
            }
        }

      + metadata_options (known after apply)

      + network_interface {
          + index              = (known after apply)
          + ip_address         = (known after apply)
          + ipv4               = true
          + ipv6               = (known after apply)
          + ipv6_address       = (known after apply)
          + mac_address        = (known after apply)
          + nat                = true
          + nat_ip_address     = (known after apply)
          + nat_ip_version     = (known after apply)
          + security_group_ids = (known after apply)
          + subnet_id          = (known after apply)
        }

      + placement_policy (known after apply)

      + resources {
          + core_fraction = 50
          + cores         = 2
          + memory        = 2
        }

      + scheduling_policy (known after apply)
    }

  # yandex_vpc_network.develop will be created
  + resource "yandex_vpc_network" "develop" {
      + created_at                = (known after apply)
      + default_security_group_id = (known after apply)
      + folder_id                 = (known after apply)
      + id                        = (known after apply)
      + labels                    = (known after apply)
      + name                      = "develop"
      + subnet_ids                = (known after apply)
    }

  # yandex_vpc_subnet.develop will be created
  + resource "yandex_vpc_subnet" "develop" {
      + created_at     = (known after apply)
      + folder_id      = (known after apply)
      + id             = (known after apply)
      + labels         = (known after apply)
      + name           = "develop-ru-central1-a"
      + network_id     = (known after apply)
      + v4_cidr_blocks = [
          + "10.1.1.0/24",
        ]
      + v6_cidr_blocks = (known after apply)
      + zone           = "ru-central1-a"
    }

Plan: 10 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + vm_details = {
      + clickhouse = {
          + hostname = "clickhouse"
          + ip       = (known after apply)
          + metadata = {
              + serial-port-enable = "1"
              + user-data          = <<-EOT
                    #cloud-config
                    users:
                      - name: ubuntu
                        shell: /bin/bash
                        sudo: ["ALL=(ALL) NOPASSWD:ALL"]
                        ssh_authorized_keys:
                          - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQA= sypchik@Mirror
                    package_update: true
                    package_upgrade: true
                    packages:
                      - libsoup2.4-1
                      - libappstream4
                      - python3
                      - python3-pip
                      - curl
                      - net-tools
                      - ca-certificates
                      - apt-transport-https
                      - gnupg
                EOT
            }
          + name     = "ch-hw"
        }
      + lighthouse = {
          + hostname = "lighthouse"
          + ip       = (known after apply)
          + metadata = {
              + serial-port-enable = "1"
              + user-data          = <<-EOT
                    #cloud-config
                    users:
                      - name: ubuntu
                        shell: /bin/bash
                        sudo: ["ALL=(ALL) NOPASSWD:ALL"]
                        ssh_authorized_keys:
                          - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQVj0IppI5Z2oG9BK4vxJXRL8= sypchik@Mirror
                    package_update: true
                    package_upgrade: true
                    packages:
                      - libsoup2.4-1
                      - libappstream4
                      - python3
                      - python3-pip
                      - curl
                      - net-tools
                      - ca-certificates
                      - apt-transport-https
                      - gnupg
                EOT
            }
          + name     = "lh-hw"
        }
      + vector     = {
          + hostname = "vector"
          + ip       = (known after apply)
          + metadata = {
              + serial-port-enable = "1"
              + user-data          = <<-EOT
                    #cloud-config
                    users:
                      - name: ubuntu
                        shell: /bin/bash
                        sudo: ["ALL=(ALL) NOPASSWD:ALL"]
                        ssh_authorized_keys:
                          - ssh-rsa GzEZm/Ha/K8YpRPajVAede7d2Vj0IppI5Z2oG9BK4vxJXRL8= sypchik@Mirror
                    package_update: true
                    package_upgrade: true
                    packages:
                      - libsoup2.4-1
                      - libappstream4
                      - python3
                      - python3-pip
                      - curl
                      - net-tools
                      - ca-certificates
                      - apt-transport-https
                      - gnupg
                EOT
            }
          + name     = "vector-hw"
        }
    }
yandex_vpc_network.develop: Creating...
yandex_vpc_network.develop: Creation complete after 3s [id=enpsb1ao4r1r89i2d54g]
yandex_vpc_subnet.develop: Creating...
yandex_vpc_subnet.develop: Creation complete after 1s [id=e9be7cpdl52ok14jlggp]
yandex_compute_instance.vm["clickhouse"]: Creating...
yandex_compute_instance.vm["vector"]: Creating...
yandex_compute_instance.vm["lighthouse"]: Creating...
yandex_compute_instance.vm["lighthouse"]: Still creating... [7s elapsed]
yandex_compute_instance.vm["clickhouse"]: Still creating... [7s elapsed]
yandex_compute_instance.vm["vector"]: Still creating... [7s elapsed]
yandex_compute_instance.vm["vector"]: Still creating... [17s elapsed]
yandex_compute_instance.vm["lighthouse"]: Still creating... [17s elapsed]
yandex_compute_instance.vm["clickhouse"]: Still creating... [17s elapsed]
yandex_compute_instance.vm["clickhouse"]: Still creating... [27s elapsed]
yandex_compute_instance.vm["lighthouse"]: Still creating... [27s elapsed]
yandex_compute_instance.vm["vector"]: Still creating... [27s elapsed]
yandex_compute_instance.vm["lighthouse"]: Still creating... [35s elapsed]
yandex_compute_instance.vm["clickhouse"]: Still creating... [35s elapsed]
yandex_compute_instance.vm["vector"]: Still creating... [35s elapsed]
yandex_compute_instance.vm["vector"]: Creation complete after 42s [id=fhmvgsqkqqvh1i014342]
yandex_compute_instance.vm["clickhouse"]: Still creating... [45s elapsed]
yandex_compute_instance.vm["lighthouse"]: Still creating... [45s elapsed]
yandex_compute_instance.vm["lighthouse"]: Still creating... [55s elapsed]
yandex_compute_instance.vm["clickhouse"]: Still creating... [55s elapsed]
yandex_compute_instance.vm["clickhouse"]: Creation complete after 58s [id=fhmj3jvm44hf47ieli1j]
yandex_compute_instance.vm["lighthouse"]: Still creating... [1m2s elapsed]
yandex_compute_instance.vm["lighthouse"]: Creation complete after 1m5s [id=fhmeou9bme2m7en50f03]
null_resource.wait_for_cloud_init["vector"]: Creating...
null_resource.wait_for_cloud_init["lighthouse"]: Creating...
null_resource.wait_for_cloud_init["clickhouse"]: Creating...
null_resource.wait_for_cloud_init["vector"]: Provisioning with 'remote-exec'...
null_resource.wait_for_cloud_init["clickhouse"]: Provisioning with 'remote-exec'...
null_resource.wait_for_cloud_init["lighthouse"]: Provisioning with 'remote-exec'...
null_resource.wait_for_cloud_init["vector"] (remote-exec): Connecting to remote host via SSH...
null_resource.wait_for_cloud_init["vector"] (remote-exec):   Host: 89.169.158.158
null_resource.wait_for_cloud_init["vector"] (remote-exec):   User: ubuntu
null_resource.wait_for_cloud_init["vector"] (remote-exec):   Password: false
null_resource.wait_for_cloud_init["vector"] (remote-exec):   Private key: true
null_resource.wait_for_cloud_init["vector"] (remote-exec):   Certificate: false
null_resource.wait_for_cloud_init["vector"] (remote-exec):   SSH Agent: false
null_resource.wait_for_cloud_init["vector"] (remote-exec):   Checking Host Key: false
null_resource.wait_for_cloud_init["vector"] (remote-exec):   Target Platform: unix
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec): Connecting to remote host via SSH...
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   Host: 89.169.129.37
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   User: ubuntu
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   Password: false
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   Private key: true
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   Certificate: false
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   SSH Agent: false
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   Checking Host Key: false
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   Target Platform: unix
null_resource.wait_for_cloud_init["lighthouse"] (remote-exec): Connecting to remote host via SSH...
null_resource.wait_for_cloud_init["lighthouse"] (remote-exec):   Host: 89.169.132.53
null_resource.wait_for_cloud_init["lighthouse"] (remote-exec):   User: ubuntu
null_resource.wait_for_cloud_init["lighthouse"] (remote-exec):   Password: false
null_resource.wait_for_cloud_init["lighthouse"] (remote-exec):   Private key: true
null_resource.wait_for_cloud_init["lighthouse"] (remote-exec):   Certificate: false
null_resource.wait_for_cloud_init["lighthouse"] (remote-exec):   SSH Agent: false
null_resource.wait_for_cloud_init["lighthouse"] (remote-exec):   Checking Host Key: false
null_resource.wait_for_cloud_init["lighthouse"] (remote-exec):   Target Platform: unix
local_file.ansible_inventory: Creating...
local_file.ansible_inventory: Creation complete after 0s [id=bb0158e6223740aa43afbc9e1288167a5c97cb05]
null_resource.wait_for_cloud_init["vector"] (remote-exec): Connected!
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): .
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec): Connecting to remote host via SSH...
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   Host: 89.169.129.37
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   User: ubuntu
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   Password: false
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   Private key: true
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   Certificate: false
null_resource.wait_for_cloud_init["clickhouse"] (remote-exec):   SSH Agent: false

null_resource.wait_for_cloud_init["clickhouse"] (remote-exec): status: done
null_resource.wait_for_cloud_init["lighthouse"] (remote-exec): .
null_resource.wait_for_cloud_init["vector"] (remote-exec): status: done

null_resource.wait_for_cloud_init["lighthouse"] (remote-exec): status: done
null_resource.wait_for_cloud_init["lighthouse"]: Creation complete after 3m50s [id=602441383948819929]
null_resource.ansible_apply: Creating...
null_resource.ansible_apply: Provisioning with 'local-exec'...
null_resource.ansible_apply (local-exec): Executing: ["/bin/sh" "-c" "      ansible-playbook -i ./ansible/inventory/hosts.yaml ./ansible/playbooks/svc.yml\n"]

null_resource.ansible_apply (local-exec): PLAY [Install Clickhouse] ******************************************************

null_resource.ansible_apply (local-exec): TASK [Gathering Facts] *********************************************************
null_resource.ansible_apply (local-exec): ok: [clickhouse]

null_resource.ansible_apply (local-exec): TASK [Download and add Clickhouse GPG key] *************************************
null_resource.ansible_apply (local-exec): changed: [clickhouse]

null_resource.ansible_apply (local-exec): TASK [Add Clickhouse repository] ***********************************************
null_resource.ansible_apply: Still creating... [8s elapsed]
null_resource.ansible_apply (local-exec): changed: [clickhouse]

null_resource.ansible_apply (local-exec): TASK [Update apt cache] ********************************************************
null_resource.ansible_apply: Still creating... [18s elapsed]
null_resource.ansible_apply (local-exec): ok: [clickhouse]

null_resource.ansible_apply (local-exec): TASK [Install clickhouse packages] *********************************************
null_resource.ansible_apply: Still creating... [28s elapsed]
null_resource.ansible_apply (local-exec): changed: [clickhouse]

null_resource.ansible_apply (local-exec): TASK [Flush handlers] **********************************************************

null_resource.ansible_apply (local-exec): RUNNING HANDLER [Start clickhouse service] *************************************
null_resource.ansible_apply: Still creating... [35s elapsed]
null_resource.ansible_apply (local-exec): changed: [clickhouse]

null_resource.ansible_apply (local-exec): TASK [Create database] *********************************************************
null_resource.ansible_apply (local-exec): changed: [clickhouse]

null_resource.ansible_apply (local-exec): PLAY [Install Vector] **********************************************************

null_resource.ansible_apply (local-exec): TASK [Gathering Facts] *********************************************************
null_resource.ansible_apply: Still creating... [45s elapsed]
null_resource.ansible_apply (local-exec): ok: [vector]

null_resource.ansible_apply (local-exec): TASK [Download Vector deb package] *********************************************
null_resource.ansible_apply (local-exec): changed: [vector]

null_resource.ansible_apply (local-exec): TASK [Install Vector] **********************************************************
null_resource.ansible_apply: Still creating... [55s elapsed]
null_resource.ansible_apply: Still creating... [1m2s elapsed]
null_resource.ansible_apply (local-exec): changed: [vector]

null_resource.ansible_apply (local-exec): TASK [Deploy Vector configuration] *********************************************
null_resource.ansible_apply (local-exec): changed: [vector]

null_resource.ansible_apply (local-exec): RUNNING HANDLER [Restart Vector] ***********************************************
null_resource.ansible_apply (local-exec): changed: [vector]

null_resource.ansible_apply (local-exec): PLAY [Install LighHouse] *******************************************************

null_resource.ansible_apply (local-exec): TASK [Gathering Facts] *********************************************************
null_resource.ansible_apply: Still creating... [1m12s elapsed]
null_resource.ansible_apply (local-exec): ok: [lighthouse]

null_resource.ansible_apply (local-exec): TASK [Install dependencies] ****************************************************
null_resource.ansible_apply: Still creating... [1m22s elapsed]
null_resource.ansible_apply: Still creating... [1m29s elapsed]
null_resource.ansible_apply (local-exec): changed: [lighthouse]

null_resource.ansible_apply (local-exec): TASK [Clone the lighthouse repository] *****************************************
null_resource.ansible_apply (local-exec): changed: [lighthouse]

null_resource.ansible_apply (local-exec): PLAY RECAP *********************************************************************
null_resource.ansible_apply (local-exec): clickhouse                 : ok=7    changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
null_resource.ansible_apply (local-exec): lighthouse                 : ok=3    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
null_resource.ansible_apply (local-exec): vector                     : ok=5    changed=4    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

null_resource.ansible_apply: Creation complete after 1m37s [id=1673328499058537998]

Apply complete! Resources: 10 added, 0 changed, 0 destroyed.

Outputs:

vm_details = {
  "clickhouse" = {
    "hostname" = "clickhouse"
    "ip" = "89.169.129.37"
    "metadata" = tomap({
      "serial-port-enable" = "1"
      "user-data" = <<-EOT
      #cloud-config
      users:
        - name: ubuntu
          shell: /bin/bash
          sudo: ["ALL=(ALL) NOPASSWD:ALL"]
          ssh_authorized_keys:
            - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCW8VMQj1Ytwl2DVRv8/4WRRB6GzEZm/Ha/K8YpRPajVAede7d2Vj0IppI5Z2oG9BK4vxJXRL8= sypchik@Mirror
      package_update: true
      package_upgrade: true
      packages:
        - libsoup2.4-1
        - libappstream4
        - python3
        - python3-pip
        - curl
        - net-tools
        - ca-certificates
        - apt-transport-https
        - gnupg

      EOT
    })
    "name" = "ch-hw"
  }
  "lighthouse" = {
    "hostname" = "lighthouse"
    "ip" = "89.169.132.53"
    "metadata" = tomap({
      "serial-port-enable" = "1"
      "user-data" = <<-EOT
      #cloud-config
      users:
        - name: ubuntu
          shell: /bin/bash
          sudo: ["ALL=(ALL) NOPASSWD:ALL"]
          ssh_authorized_keys:
            - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCW8VMQj1Ytwl2DVRv8/79V6g5V18VtqHwutoc7bQM+QO2eQ3p09I0Afx4WRRB6GzEZm/Ha/K8YpRPajVAede7d2Vj0IppI5Z2oG9BK4vxJXRL8= sypchik@Mirror
      package_update: true
      package_upgrade: true
      packages:
        - libsoup2.4-1
        - libappstream4
        - python3
        - python3-pip
        - curl
        - net-tools
        - ca-certificates
        - apt-transport-https
        - gnupg

      EOT
    })
    "name" = "lh-hw"
  }
  "vector" = {
    "hostname" = "vector"
    "ip" = "89.169.158.158"
    "metadata" = tomap({
      "serial-port-enable" = "1"
      "user-data" = <<-EOT
      #cloud-config
      users:
        - name: ubuntu
          shell: /bin/bash
          sudo: ["ALL=(ALL) NOPASSWD:ALL"]
          ssh_authorized_keys:
            - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCW8VMQj1Ytwl2DVRv8//Ha/K8YpRPajVAede7d2Vj0IppI5Z2oG9BK4vxJXRL8= sypchik@Mirror
      package_update: true
      package_upgrade: true
      packages:
        - libsoup2.4-1
        - libappstream4
        - python3
        - python3-pip
        - curl
        - net-tools
        - ca-certificates
        - apt-transport-https
        - gnupg

      EOT
    })
    "name" = "vector-hw"
  }
}
sypchik@Mirror:/mnt/c/Users/Sypchik/Desktop/home work/ansible/mnt-homeworks/08-ansible-03-yandex$
```

Vector
```
sypchik@Mirror:/mnt/c/Users/Sypchik/Desktop/home work/ansible/mnt-homeworks/08-ansible-03-yandex$ ssh ubuntu@89.169.158.158
Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 5.4.0-198-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro
New release '22.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Sat Nov  2 22:16:54 2024 from 94.25.229.135
ubuntu@vector:~$ vector validate /etc/vector/vector.yaml
Loaded with warnings ["/etc/vector/vector.yaml"]
------------------------------------------------
~ Transform "parse_logs" has no consumers

x Could not create subdirectory "validate_tmp" inside of data dir "/var/lib/vector/": Permission denied (os error 13)
ubuntu@vector:~$ sudo chmod -R 777 /var/lib/vector/
ubuntu@vector:~$ vector validate /etc/vector/vector.yaml
Loaded with warnings ["/etc/vector/vector.yaml"]
------------------------------------------------
~ Transform "parse_logs" has no consumers

√ Component configuration
√ Health check "print"
------------------------------------------------
                                       Validated
ubuntu@vector:~$
```

lighhouse
```
sypchik@Mirror:/mnt/c/Users/Sypchik/Desktop/home work/ansible/mnt-homeworks/08-ansible-03-yandex$ ssh ubuntu@89.169.132.53
Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 5.4.0-198-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro
New release '22.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Sat Nov  2 22:17:18 2024 from 94.25.229.135
ubuntu@lighthouse:~$ w3m /opt/lighthouse/index.html

```

Clickhouse
```
sypchik@Mirror:/mnt/c/Users/Sypchik/Desktop/home work/ansible/mnt-homeworks/08-ansible-03-yandex$ ssh ubuntu@89.169.129.37
Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 5.4.0-198-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro
New release '22.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Sat Nov  2 22:16:23 2024 from 94.25.229.135
ubuntu@clickhouse:~$ clickhouse-client
ClickHouse client version 24.10.1.2812 (official build).
Connecting to localhost:9000 as user default.
Connected to ClickHouse server version 24.10.1.

Warnings:
 * Maximum number of threads is lower than 30000. There could be problems with handling a lot of simultaneous queries.
 * Linux threads max count is too low. Check /proc/sys/kernel/threads-max
 * Available memory at server startup is too low (2GiB).

clickhouse.ru-central1.internal :) exit
Bye.
ubuntu@clickhouse:~$
```
Ниже приведены скрины с запущенными сервисами

![Screenshot 2024-11-03 012234](https://github.com/user-attachments/assets/375d5e31-c7c2-4890-a3d5-4901227e28f3)

![Screenshot 2024-09-16 215645](https://github.com/user-attachments/assets/cbf05bf9-0a88-4ed2-8ae7-8a67e73963e1)


