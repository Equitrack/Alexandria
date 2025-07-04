
# Monitoreo

El **monitoreo** es el proceso de supervisar y verificar el estado de los sistemas y recursos de hardware y software en una infraestructura de TI, para asegurar que funcione de forma correcta.

Sirve para anticipar y detectar problemas que afectan el rendimiento y disponibilidad de la infraestructura.

| Tecnología | Descripción                                                                                                                                                                |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Monitoreo  | Se enfoca en la supervisión constante de la infraestructura, recopilando métricas en tiempo real.                                                                          |
| Loggings   | Se enfoca en la recolección y almacenamiento de registros generados por aplicaciones y sistemas. Se utilizan normalmente para la depuración y análisis de eventos pasados. |
Métricas clave para el monitoreo:

- Hardware: CPU, memoria, almacenamiento, red.
- Software: Número de peticiones, tiempo de respuesta, tasas de error, estado de los servicios.

Las **alertas** son un mecanismo que se activa cuando una métrica monitorizada alcanza un umbral definido, lo cual indica que algo no funciona como debería.

**Prometheus** es una herramienta de monitoreo, almacena métricas y gestiona los datos en tiempo real, recolecta la información usando **scraping**, consultando la información de los endpoints en intervalos de tiempo.

Elementos principales de prometheus:

- Scraper: Sondea los endpoints/targets (objetivos a monitorear) en intervalos de tiempo. 
- Base de datos: Almacena métricas en series temporales (como rotación de logs).
- PromQL: Es el lenguaje de consultas de prometheus, se puede usar expresiones regulares.
- Exporters: Son componentes que exponen métricas para que prometheus los pueda recoletar, se instalan en los endpoints.

Crear una alerta: definir la regla en el archivo rules.yaml con una expresión PromQL
	- Nombre.
	- Expresión PromQL que define la condición de la alerta.
	- Tiempo que debe mantenerse la condición para activar la alerta (opcional).
	- Información adicional sobre la alerta.

> Prometheus evalua estas reglas en intervalos de tiempo (30s por ejemplo) y se puede integrar con otras tecnologías como alertmanage

Para el monitoreo de un clúster de kubernetes es una buena idea usar el objeto **DaemonSet** para desplegar exporters y autoescalen cuando se agregan nodos.