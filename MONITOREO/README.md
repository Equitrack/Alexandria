
# Monitoreo

El monitoreo es el proceso de supervisar y verificar el estado de los sistemas y recursos de hardware y software en una infraestructura de TI, para asegurar que funcione de forma correcta.

Sirve para anticipar y detectar problemas que afectan el rendimiento y disponibilidad de la infraestructura.

| Tecnología | Descripción                                                                                                                                                                |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Monitoreo  | Se enfoca en la supervisión constante de la infraestructura, recopilando métricas en tiempo real.                                                                          |
| Loggings   | Se enfoca en la recolección y almacenamiento de registros generados por aplicaciones y sistemas. Se utilizan normalmente para la depuración y análisis de eventos pasados. |
Métricas clave para el monitoreo:

- Hardware: CPU, Memoria, Almacenamiento, Red
- Software: Rendimiento, Nú

Para el monitoreo de un clúster de kubernetes es una buena idea usar el objeto **DaemonSet** para desplegar exporters y autoescalen cuando se agregan nodos.