## Software Managment

A package management system is a collection of tools to automate the process of installing, upgrading, configuring, and removing software packages from a computer.

Red Hat based:
- RPM (Red Hat Package Manager)
- YUM (The Yellow dog Updater, Modified)
- DNF 

| Commands                                                                    |
| --------------------------------------------------------------------------- |
| `install <paquete>` → Instala un paquete.                                   |
| `update <paquete>` → Actualiza paquetes (si omites nombre, actualiza todo). |
| `upgrade` → Igual que `update` pero maneja reemplazos obsoletos.            |
| `remove <paquete>` → Elimina paquete(s).                                    |
| `search <paquete>` → Busca por nombre/descripción.                          |
| `info <paquete>` → Muestra detalles de un paquete.                          |
| `list installed` → Lista lo instalado.                                      |
| `clean all` → Limpia cachés y metadatos.                                    |
En **RPM** no hay una opción de purga.

```bash
rpm -qc paquete   # Lista archivos de configuración del paquete
rpm -ql paquete   # Lista todos los archivos instalados por el paquete
```

Debian based:
- APT (The Advanced Packaging Tool)
- DPKG

| Commands                                                             |
| -------------------------------------------------------------------- |
| `install <paquete>` → Instala un paquete.                            |
| `remove <paquete>` → Elimina un paquete (pero deja config).          |
| `purge <paquete>` → Elimina paquete y configuración.                 |
| `update` → Actualiza índices de paquetes desde repositorios.         |
| `upgrade` → Actualiza todos los paquetes instalados.                 |
| `full-upgrade` → Actualiza y permite eliminar/instalar dependencias. |
| `autoremove` → Elimina dependencias huérfanas.                       |
| `search <paquete>` → Busca paquetes en repositorios.                 |
| `show <paquete>` → Muestra información detallada.                    |
| `list --installed` → Lista los paquetes instalados.                  |
| `clean` → Limpia archivos descargados.                               |

## Alternatives

Alternatives is a **system management tool** used when you have multiple programs that provide the same functionality or different versions.

For example, you may have different versions of python.
With alternatives, you can switch which version is set as the default.

```bash
/usr/bin/python2.7
/usr/bin/python3.8
/usr/bin/python3.10
/usr/bin/python3.11

sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.7 10
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.8 20
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.10 30
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.11 40

sudo update-alternatives --config python
```

```
There are 4 choices for the alternative python (providing /usr/bin/python).

  Selection    Path                Priority   Status
------------------------------------------------------------
* 0            /usr/bin/python3.11  40        auto mode
  1            /usr/bin/python2.7   10        manual mode
  2            /usr/bin/python3.8   20        manual mode
  3            /usr/bin/python3.10  30        manual mode
  4            /usr/bin/python3.11  40        manual mode

Press <enter> to keep the current choice[*], or type selection number:

# For example, you select 3
```

```bash
python --version
Python 3.10
```

```bash
# Registrar nuevas versiones
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.8 20
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.10 30

# Ver alternativas disponibles
update-alternatives --list python

# Elegir versión manualmente
sudo update-alternatives --config python

# Forzar una versión específica
sudo update-alternatives --set python /usr/bin/python3.10

# Poner en modo automático
sudo update-alternatives --auto python
```

