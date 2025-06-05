## ¿Qué es Docker?

Docker es una tecnología open source que permite crear, ejecutar y administrar contenedores.

Un contenedor es un entorno de ejecución ligero y aislado que ejecuta una aplicación con todas sus dependencias (microservicios).

La diferencia entre una máquina virtual y un contenedor, es que una máquina virtual se ejecuta sobre un hipervisor (como VMware, Hyper-V o KVM). El hipervisor es un mediador de las instrucciones que van al hardware físico.

Un contenedor se ejecuta sobre un sistema operativo, comparte el kernel y utliiza tecnologías como namespaces y cgroups.

> namespaces: crean espacios aislados para procesos, red, usuarios y sistema de archivos. <br>
> cgroups: controlan y limitan el uso de recursos como CPU, memoria y disco.

## CMD vs ENTRYPOINT

CMD se usa para definir la ejecución de un programa o script y opcionalmente parámetros, los parámetros pueden ser sobreescritos al crear el contenedor.

ENTRYPOINT es para definir la ejecución de un programa o script que siempre se ejecutará en el contenedor, no puede sobreescribirse, pero se pueden agregar parámetros al crear el contenedor.

