# Домашнее задание к занятию 2. «Применение принципов IaaC в работе с виртуальными машинами»

## Задача 1

### Установил всё необходимое ПО. Освоим проброс портов и авторизацию в yandex cloud по токену, без браузера на ВМ с Linux.

## Задача 2

### Научился создавать ВМ при помощи Vagrant. Научился редактировать VagrantFile, запомнил основные команды vagrant.

## Задача 3

### Создал образ Debian 12 при помощи Packer. Поднял ВМ с данным образом.
### Mydebian.json: {
    "builders": [
        {
            "type": "yandex",
            "token": "xxx",
            "folder_id": "b1gdvgojd36qgffk0tnj",
            "zone": "ru-central1-d",
            "image_name": "debian-12-docker",
            "image_description": "my custom debian with docker",
            "source_image_family": "debian-12",
            "source_image_folder_id": "standard-images",
            "subnet_id": "fl81r5ieank0m2g19tut",
            "use_ipv4_nat": true,
            "disk_type": "network-hdd",
            "ssh_username": "debian"
        }
    ],
    "provisioners": [
        {
            "type": "shell",
            "inline": [
                "echo 'hello from packer'"
            ]
        },
        {
           "type": "shell",
           "script": "scripts/install-docker.sh"
        },
        {
      "type": "shell",
      "inline": ["docker --version", "docker compose version"]
        }
    ]
}
