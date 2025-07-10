
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

La alta disponibilidad es importante para ambientes productivos.

Prometheus federation es una opción para tener concurrencia, el problema es que en una arquitectura con varias instancias solo una de ellas tiene el concentrado de las métricas.

Thanos es una buena opción, sincroniza la información de las métricas y se pueden consultar a las instancias de prometheus o thanos quertier.

Thanos se divide en dos elementos importantes:

- Thanos cliente (thanos sidecard)
- Thanor server (thanos querier)

Requerimientos:

- Thanos sidecar requiere almacenamiento de objetos como S3 o MinIO.
- Thanos sidecar requiere acceso a los datos `/prometheus` y a la API de prometheus `http://prometheus:9090` (un sidecard por cada instancia de prometheus).
- Thanos querier (solo se instala uno) requiere comunicación con los múltiples thanos sidecard.

# Recomendaciones

Se recomienza consumir **thanos querier** cuando las instancias de prometheus están distribuidas de forma geográfica.

Se recomienda usar un **balanceador de carga** en las **instancias de prometheus** si están en la misma zona geográfica para tener una latencia menor y disfrubuir el uso de recursos.

> Es más amigable la configuración entre grafana y el load balancer.


## Optimizar consultas en prometheus

Usar **agregaciones, recording y evitar la menor granularidad** (consultas con pocos filtros o ninguno).

Las agregaciones en Prometheus son operaciones que resumen o agrupan datos para reducir su volumen y hacer las consultas más eficientes y legibles.

|Función|Qué hace|Ejemplo|
|---|---|---|
|`sum()`|Suma los valores|`sum(rate(http_requests_total[5m]))`|
|`avg()`|Promedia los valores|`avg(rate(cpu_usage_seconds_total[5m]))`|
|`max()`|Muestra el valor máximo|`max(memory_usage_bytes)`|
|`min()`|Muestra el valor mínimo|`min(disk_io_bytes_total)`|
|`count()`|Cuenta cuántas series coinciden|`count(up)`|
|`stddev()`|Desviación estándar|`stddev(rate(request_duration_seconds[5m]))`|
|`topk(k, ...)`|Muestra las _k_ series con mayor valor|`topk(3, rate(http_requests_total[1m]))`
También permite agrupar los datos según etiquetas como `job`, `instance`, `status`, etc

Recording Rules para Preprocesar Consultas: Estas reglas calculan métricas de forma anticipada y las almacenan, lo que permite consultas más rápidas.

```
groups:
  - name: example-rules
    rules:
      - record: job:http_requests_total:rate5m
        expr: rate(http_requests_total[5m])
```



Usar una menor granularidad si los datos más finos no son necesarios.

Evita consultas costosas como aquellas que no agregan filtros, o aquellas que no son necesarias en una vista general. Esto incluye no hacer consultas de métricas sin filtros o hacer operaciones en grandes rangos de datos.

Julio 2025 - Escenario de práctica:

https://killercoda.com/thanos/scenario/1-globalview

Desviación estándar (rangos): 50ms (excelente), 100ms (bueno) 200ms (regular)

# Prometheus

Latencia `http_request_duration_seconds`

Tráfico `http_requests_total`

Errores `http_requests_total{status=~"5.."}`

Saturación `node_cpu_seconds_total` `memory_usage_bytes` `disk_io_bytes_total`