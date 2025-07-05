
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
	- Nobre de la alerta
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

Usar Thanos con Prometheus para alta disponibilidad.

Thanos se divide en dos elementos importantes:

- Thanos cliente (thanos sidecard)
- Thanor server (thanos quertier)

----

Hi Karen,

Thank you for your message.

I'm interested in this position and would to hear more details about the role and expectations.

I'm available for a call on Monday if that works for you. Please let me know what time would be convenient.

Best regards,  
Antonio