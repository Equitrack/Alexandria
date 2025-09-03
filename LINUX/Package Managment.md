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

Alternatives is a tool management programs when you have multiple programs at the same function or versions.