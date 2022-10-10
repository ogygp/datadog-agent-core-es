![](https://datadog-docs.imgix.net/img/dd_logo_n_70x75.png)

# Bienvenido a Datadog !

## Requerimientos preliminares para monitoreo con Datadog

### **Agente:**

El Agente es un software ligero que se ejecuta en sus hosts. Recopila eventos y métricas de los hosts y los envía a Datadog. El tráfico siempre es iniciado del Agente hacia Datadog. Nunca se inician sesiones desde Datadog hacia el Agente. 
Ver [Overhead del Agente](https://docs.datadoghq.com/agent/basic_agent_usage/?tab=agentv6v7#agent-overhead).

- **Acceso a Internet - Puertos y reglas de firewall** : 
  - **Outbound** : Todo el tráfico outbound se envía por SSL a través de TCP/UDP
    - 443/TCP - Envío de la mayoría de los datos del Agente (métricas, trazas, procesos/contenedores vivos).
    - 123/UDP - Sincronización con servidores NTP de Datadog
    - 10516/TCP - Envío de datos de logs. Es posible configurar el Agente para hacer el envío por HTTPS como se menciona [aquí](https://docs.datadoghq.com/logs/guide/log-collection-troubleshooting-guide/#outbound-traffic-on-port-10516-is-blocked).
    
  - **Inbound (tráfico local)** : Se utilizan para los servicios del Agente que se comunican entre sí localmente dentro del host solamente.
    - 5000/TCP - Go\_Expvar
    - 5001/TCP - IPC API
    - 5002/TCP - GUI
    - 8121/TCP - Dogstatsd
    - 8126/TCP - Tracing
  - Indicar en whitelist de su firewall(s) **\*.datadoghq.com** (esto es, permiso de wildcard sobre el puerto **443/TCP** para la URL: \*.datadoghq.com)

     Para mayor detalle ver: [https://docs.datadoghq.com/agent/guide/network/?tab=agentv6](https://docs.datadoghq.com/agent/guide/network/?tab=agentv6)

- **Acceso restringido** 
  - **Configuración Agente/Proxy:** Si la configuración de su red restringe el tráfico de salida, se puede considerar la configuración de un proxy para enviar todo el tráfico del Agente hacia Datadog. Para mayor detalle ver: [https://docs.datadoghq.com/agent/proxy/?tab=agentv6#using-haproxy-as-a-proxy](https://docs.datadoghq.com/agent/proxy/?tab=agentv6#using-haproxy-as-a-proxy)
- Consulte la documentación del Agente para ver las **Plataformas de Sistema Operativo soportadas** [https://docs.datadoghq.com/agent/basic\_agent\_usage/?tab=agentv6v7#supported-os-versions](https://docs.datadoghq.com/agent/basic_agent_usage/?tab=agentv6v7#supported-os-versions)

**Integraciones:**

Una integración, en el nivel más alto, es cuando se ensambla un sistema unificado a partir de unidades que generalmente se consideran por separado. En Datadog, puede usar integraciones para reunir todas las métricas y logs de su infraestructura y obtener información sobre el sistema unificado como un todo. 
Consulte la [Lista de Integraciones de Datadog](https://docs.datadoghq.com/integrations/)

---

💡 **Las integraciones específicas a utilizar se determinan de acuerdo al requerimiento particular de cada cliente**