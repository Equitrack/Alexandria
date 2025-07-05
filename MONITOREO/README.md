
# Monitoreo

El **monitoreo** es el proceso de supervisar y verificar el estado de los sistemas y recursos de hardware y software en una infraestructura de TI, para asegurar que funcione de forma correcta.

El objetivo es anticipar y detectar problemas que afectan el rendimiento y disponibilidad de la infraestructura.

| Proceso   | Descripción                                                                                                                                                  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Monitoreo | Se enfoca en la supervisión constante de la infraestructura, recopilando métricas en tiempo real.                                                            |
| Loggings  | Se enfoca en el almacenamiento de registros generados por aplicaciones y sistemas. Se utilizan normalmente para la depuración y análisis de eventos pasados. |
| Métricas  | Son registros numéricos generados de forma constante.                                                                                                        |
| Logs      | Son registros más detallados que se almacenan para analizar.                                                                                                 |

Métricas clave para el monitoreo:

- Hardware: CPU, memoria, almacenamiento, red.
- Software: Número de peticiones, tiempo de respuesta, tasas de error, estado de los servicios.

**Prometheus** es una herramienta de monitoreo que almacena métricas y gestiona los datos en tiempo real, recolecta la información en intervalos de tiempo.

Elementos principales de prometheus:

- Scraper: Sondea los endpoints/targets (objetivos a monitorear) en intervalos de tiempo. 
- Base de datos: Almacena métricas en series temporales (como rotación de logs).
- PromQL: Es el lenguaje de consultas de prometheus, se puede usar expresiones regulares, funciones y condicionales.
- Exporters: Son componentes que exponen métricas para que prometheus las pueda recoletar, se instalan en los endpoints.

Las **alertas** son un mecanismo que se activa cuando una métrica monitorizada alcanza un umbral definido, lo cual indica que algo no funciona como debería.

Se pueden crear alertas en prometheus y se require lo siguiente:

- Nombre de la alerta
- Expresión PromQL que define la condición de la alerta.
- Tiempo que debe mantenerse la condición para activar la alerta (opcional).
- Información adicional sobre la alerta.

```yaml
# EJEMPLO (suele ser más complejo)
groups:
 - name: exmaple-alert
   rules:
   - alert: HighCpuUsege
     expr: cpu_usage > 0.9
     for: 5min
     anotations:
	   description: "El uso de CPU ha superado el 90% durante 5min"
```

Prometheus evalua estas reglas en intervalos de tiempo (30s por ejemplo) y se puede integrar con otras tecnologías como alertmanager para enviar las alertas por correo o aplicaciones como slack o discord.

**Grafana** es una herramienta popular para el monitoreo de aplicaciones, se encarga de repesentar la información de forma gráfica a través de dashboards, estos se pueden crear o importar.

Grafana no recolecta métricas, solo las consulta de otras herramientas como prometheus.

Algunos **exporters** populares:

- NodeExporter: Está enfocado a sistemas operativos
- cAdvisor: Está enfocado a contenedores
- Kube-State-Metrics: Está enfocado a kubernetes y los pods (recursos, réplicas, estado)
- Prometheus Adapter: Expone métricas personalizadas de kuebernetes

Para el monitoreo de un clúster de kubernetes es una buena idea usar el objeto **DaemonSet** para desplegar exporters y se autoescalen cuando se agreguen nodos.

# Alta disponibilidad

La alta disponibilidad es importante para ambientes productivos, el uso de thanos es una buena estrategía para el correcto diseño.

Thanos se divide en dos elementos importantes:

- Thanos cliente (thanos sidecard)
- Thanor server (thanos querier)

Thanos sidecar requiere acceso a los datos y a la API de la instancia de prometheus.

Thanos querier requiere comunicación con thanos sidecard.

Sobre thanos:

- Objetivo: Thanos se encarga que en las instancias de prometheus, la información esté sincornizada.
- Federación de prometheus: La información solo está concentrada en una de las instancias, con thanos se pueden consultar todas las instancias.
- Almacenamiento: Thanos guarda en paralelo la información de las métricas recolectadas por prometheus en un objeto de almacenamiento como S3 o MinIO.
- Grafana: puede consultar la información de las métricas a thanos querier.

# Recomendaciones:

Se recomienza consumir **thanos querier** cuando las instancias de prometheus están distribuidas de forma geográfica.

Se recomienda usar un **balanceador de carga** en las **instancias de prometheus** si están en la misma zona geográfica para tener una latencia menor y disfrubuir el uso de recursos.

> Es más amigable usar grafana y el load balancer para la configuración.

Julio 2025 - Escenario de práctica:

https://killercoda.com/thanos/scenario/1-globalview



