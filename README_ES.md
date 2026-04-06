Se implementó una solución de monitoreo basada en Prometheus y Grafana, desplegada sobre máquinas virtuales, con el objetivo de centralizar métricas y brindar visibilidad operativa a los equipos mediante dashboards accesibles y personalizados.
---
Arquitectura
Flujo de datos:
Node Exporter → Prometheus → Grafana
Node Exporter: expone métricas del sistema operativo (CPU, memoria, disco, red)
Prometheus: recolecta métricas mediante scraping
Grafana: visualiza la información en dashboards
---
Implementación
1. Infraestructura
Creación de VM Linux en Azure
Configuración de reglas de red (NSG) para acceso a:
SSH (22)
Grafana (3000)
Prometheus (9090)
Node Exporter (9100)
---
2. Grafana
Instalación y configuración como servicio
Acceso web para administración y visualización
---
3. Prometheus
Instalación manual
Configuración del archivo prometheus.yml
Exposición de métricas en puerto 9090
---
4. Node Exporter
Instalación y ejecución en la VM
Exposición de métricas del sistema en /metrics
---
5. Integración
Se configuró Prometheus para recolectar métricas de Node Exporter:
job_name: "node"
static_configs:
targets: ["localhost:9100"]
Luego se integró Prometheus como Data Source en Grafana para la visualización.
---
Dashboard

Se creó un dashboard único con múltiples paneles para visualizar:
Uso de CPU (%)
Uso de memoria (%)
Memoria disponible (GB)
Uso de disco (%)
Tráfico de red (entrada/salida)
Load del sistema
Esto permite tener una visión clara y en tiempo real del estado del servidor.
---
Desafíos durante la implementación

Durante el laboratorio surgieron distintos desafíos típicos de un entorno real:
Configuración inicial de repositorios y paquetes
Ajustes en la configuración de Prometheus
Validación de conectividad entre servicios
Manejo de procesos en Linux
Organización de dashboards en Grafana
---
Conclusión
 logró desplegar un sistema funcional de monitoreo en la nube, con métricas en tiempo real y visualización centralizada.
Este tipo de arquitectura es ampliamente utilizada en entornos productivos para observabilidad y control de infraestructura.
