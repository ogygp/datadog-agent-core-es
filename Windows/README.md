![](https://datadog-docs.imgix.net/images/icons/platform_windows.png?ch=Width%2cDPR&fit=max&auto=format&w=138)

**Importante:** Antes de iniciar la instalación del Agente de Datadog por favor revise los [Requerimientos Preliminares](https://github.com/ogygp/datadog-agent-core-es/blob/main/README.md)

Se recomienda seguir las **`Instrucciones de inicio rápido (IN-APP)`**  en su instancia Datadog para obtener la mejor experiencia. Elija las instrucciones de acuerdo al `SITE` que le corresponda. 

Puede identificar en que SITE se encuentra haciendo coincidir el URL de su sitio web de Datadog con el URL del sitio en la siguiente tabla:

| SITE | SITE URL | SITE PARAMETER | LOCATION | IN-APP QUICK GUIDE|
| --- | --- | --- | --- | --- |
| US1 | `https://app.datadoghq.com` | `datadoghq.com` | US | [US1-QUICK-GUIDE](https://app.datadoghq.com/account/settings#agent/windows) |
| US3 | `https://us3.datadoghq.com` | `us3.datadoghq.com` | US |[US3-QUICK-GUIDE](https://us3.datadoghq.com/account/settings#agent/windows) |
| US5 | `https://us5.datadoghq.com` | `us5.datadoghq.com` | US |[US5-QUICK-GUIDE](https://us5.datadoghq.com/account/settings#agent/windows) |


## Instalación en Windows

Consulte la documentación del Agente para [versiones de SO soportadas](https://docs.datadoghq.com/agent/basic_agent_usage/#supported-os-versions).

A partir de la versión 6.11.0, el core y los componentes APM/trace del Agente de Windows se ejecutan bajo la cuenta `ddagentuser`, creada en el momento de la instalación, en lugar de ejecutarse bajo la cuenta `LOCAL_SYSTEM`, como ocurría en versiones anteriores. Si está actualizando desde una versión de Agente Datadog **6.x a =>6.11**, revise la información de [cambios de usuario del Agente Windows](https://docs.datadoghq.com/agent/faq/windows-agent-ddagent-user/) antes de la instalación.

Durante el proceso de instalación se le solicitará su **Datadog API KEY**. Este ya se incluye en las instrucciones de inicio rápido. Si posteriormente quiere ubicar su API Key puede navegar a **[`<DATADOG_SITE_URL>`](https://docs.datadoghq.com/getting_started/site/#access-the-datadog-site)/organization-settings/api-keys**   

---
### Nueva instalación (interactiva)

`Los parámetros de los comandos ya vienen especificados en las instrucciones de inicio rápido (IN-APP) dentro de su instancia de Datadog.`

1.  Descargue el [instalador de Datadog Agent](https://s3.amazonaws.com/ddagent-windows-stable/datadog-agent-7-latest.amd64.msi).

2.  Ejecute el instalador (como **Administrator**)

3.  Siga las instrucciones, acepte el acuerdo de licencia e introduzca su **Datadog API key**

4.  Luego introduzca su región de Datadog. (en la tabla de la sección de arriba se muestra como `SITE PARAMETER`) 

5.  Cuando la instalación termina, se le da la opción de iniciar el Datadog Agent Manager.

**Nota**: Los enlaces a todas las versiones disponibles del instalador de Windows son [proporcionados en formato JSON](https://s3.amazonaws.com/ddagent-windows-stable/installers.json)

---
### Instalación nueva (unattended)

`Los parámetros de los comandos ya vienen especificados en las instrucciones de inicio rápido (IN-APP) dentro de su instancia de Datadog.`

1.  [Descargue el instalador de Datadog Agent](https://s3.amazonaws.com/ddagent-windows-stable/datadog-agent-7-latest.amd64.msi).

2.  Ejecute uno de los siguientes comandos dentro del directorio donde descargó el instalador.

    **Comando prompt**:

    `start /wait msiexec /qn /i <instalador de Datadog Agent>.msi APIKEY="<DATADOG_API_KEY>" SITE="<DATADOG_SITE_PARAMETER>"`

    **Powershell**:

    `Start-Process -Wait msiexec -ArgumentList '/qn /i <instalador de Datadog Agent>.msi APIKEY="<DATADOG_API_KEY>" SITE="<DATADOG_SITE_PARAMETER>"'`

    `HOSTNAME` y `TAGS` son valores opcionales. Consulte la [documentación del Agente de Windows](https://docs.datadoghq.com/agent/basic_agent_usage/windows/#command-line) para conocer todas las opciones disponibles.


### Deployment en Azure

Consulte la [documentación de Datadog Azure](https://docs.datadoghq.com/integrations/azure/#setup) para desplegar el Agente en su servicio en la nube.

### Upgrade desde el Agente 5 o 6

El Agente 7 sólo soporta Python 3. Antes de actualizar, confirme que los custom checks que tiene son compatibles con Python 3. Consulte la [Guía de migración de custom checks de Python 3](https://docs.datadoghq.com/agent/guide/python-3/) para obtener más información. Si no está utilizando custom checks o ya ha confirmado su compatibilidad, puede actualizar ahora utilizando uno de los comandos siguientes.

Si está actualizando desde una versión de Agente Datadog < 5.12.0, primero actualice a una versión más reciente del Agente 5 (>= 5.12.0 pero < 6.0.0) utilizando el [instalador EXE](https://s3.amazonaws.com/ddagent-windows-stable/ddagent-cli-latest.exe) y luego actualice a la versión de Agente Datadog >= 6.

1.  Siga los pasos de la nueva instalación estándar o de línea de comandos.

### Downgrade a una versión anterior

Los downgrades automáticos no están soportados. Para hacer un downgrade, primero desinstale la versión actual y luego siga los pasos de la nueva instalación indicados anteriormente.