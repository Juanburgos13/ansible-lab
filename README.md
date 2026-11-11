# Laboratorio de Ansible con Docker

## Objetivo de la práctica

El objetivo de esta práctica es implementar un laboratorio utilizando Docker y Ansible para administrar dos servidores Ubuntu 24.04.

Mediante un Playbook se automatizan diferentes tareas, como mostrar información del servidor, identificar el sistema operativo, crear directorios y archivos, utilizar ciclos (loops) y ejecutar condiciones (when).

## Tecnologías utilizadas

- Docker
- Docker Compose
- Ansible
- Ubuntu 24.04
- Python 3

## Estructura del proyecto

```text
ansible-lab/
├── docker-compose.yml
├── inventory.ini
├── playbook.yml
└── README.md
```

## Iniciar los contenedores

Para crear e iniciar los dos servidores Docker, ejecutar:

```bash
docker compose up -d
```

Para comprobar que los contenedores están funcionando:

```bash
docker ps
```

## Instalar Python en los servidores

```bash
docker exec -it server1 bash
apt update
apt install -y python3
exit

docker exec -it server2 bash
apt update
apt install -y python3
exit
```

## Comprobar la conexión con Ansible

```bash
ansible docker -i inventory.ini -m ping
```

## Ejecutar el Playbook

Para ejecutar todas las tareas automatizadas:

```bash
ansible-playbook -i inventory.ini playbook.yml
```

## Tareas realizadas

El Playbook realiza las siguientes operaciones en ambos servidores:

1. Mostrar el nombre del servidor.
2. Mostrar el sistema operativo y su versión.
3. Crear el directorio `/tmp/ansible-demo`.
4. Crear el archivo `info.txt` con información del servidor.
5. Crear los directorios `logs`, `backup` y `config` mediante un loop.
6. Mostrar un mensaje únicamente cuando el sistema operativo sea Ubuntu, utilizando una condición `when`.

## Evidencia de ejecución

A continuación se presenta la captura de pantalla de la ejecución exitosa del Playbook en ambos servidores.

**Captura de pantalla:**

<img width="1920" height="1080" alt="Screenshot 2026-11-11 at 4 10 58 PM" src="https://github.com/user-attachments/assets/bd17539d-30d0-4e67-90d8-0cbd7556aa67" />


