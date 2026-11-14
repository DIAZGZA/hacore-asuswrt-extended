
# ASUSWRT (Extended) for Home Assistant

Una integración personalizada de Home Assistant para enrutadores ASUSWRT. Descubre dispositivos conectados al enrutador y expone rastreadores de dispositivos y sensores del enrutador, con sondeo configurable e información adicional sobre la intensidad de la señal del dispositivo (RSSI) cuando esté disponible.

Esta integración es una versión modificada de la integración ASUSWRT en [Home Assistant Core](https://www.home-assistant.io/integrations/asuswrt). Sondea el enrutador localmente; no requiere un servicio en la nube.

## Características

- Realice un seguimiento de los clientes conectados con su estado de conexión, nombre de host, dirección IP, dirección MAC y última hora de acceso.
- Exponer RSSI para los clientes cuando el método de conexión seleccionado y el enrutador lo proporcionen.
- Configure el intervalo de sondeo del enrutador (de 5 a 300 segundos; predeterminado: 30 segundos).
- Proporcionar sensores de enrutador disponibles, según protocolo, modelo y firmware:
- Recuento de dispositivos conectados, tasas de carga/descarga y totales de tráfico.
- Uso de CPU y uso por núcleo, memoria, tiempo de actividad y promedios de carga.
- Temperaturas de radio y CPU donde se admitan.
- Elija HTTP, HTTPS, SSH o Telnet para la comunicación del enrutador.
- Configurar el modo enrutador o punto de acceso para conexiones SSH/Telnet.

## Installation

Este repositorio es una integración personalizada de Home Assistant. Instale sus archivos en el directorio de componentes personalizados `asuswrt_extended`:
```bash
git clone https://github.com/pablogpz/hacore-asuswrt-extended.git \
  /config/custom_components/asuswrt_extended
```

Reemplace `/config` con el directorio de configuración de Home Assistant si es diferente. Luego reinicie Home Assistant y agregue **ASUSWRT (Extendido)** desde **Configuración → Dispositivos y servicios → Agregar integración**.

La integración declara sus requisitos de Python en `manifest.json`; Home Assistant los instala. No se requiere ningún entorno o servicio de Python independiente.

## Configuration

Agregue la integración a través de la interfaz de usuario de Home Assistant y proporcione:

- **Host**: nombre de host o dirección IP del enrutador.
- **Nombre de usuario** y autenticación: contraseña o un archivo de clave SSH para conexiones SSH. La ruta clave debe poder leerse desde el host de Home Assistant.
- **Protocolo**: HTTP, HTTPS, SSH o Telnet. Se puede suministrar un puerto opcional en configuración avanzada.
- **Modo**: para conexiones SSH/Telnet, seleccione el modo enrutador o punto de acceso.

Después de la configuración, use las opciones de integración para configurar:

| Opción | Predeterminado | Descripción |
| --- | --- | --- |
| Intervalo de escaneo del enrutador | 30 segundos | Intervalo de sondeo, configurable de 5 a 300 segundos. |
| Considere su hogar | Rastreador de dispositivos Home Assistant predeterminado | Es hora de esperar antes de marcar un dispositivo perdido. |
| Seguimiento de dispositivos desconocidos | Apagado | Incluya clientes anónimos. |
| Interfaz | `eth0` | Interfaz utilizada para estadísticas en modo SSH/Telnet. |
| dnsmasq alquila ubicación | `/var/lib/misc` | Ubicación de `dnsmasq.leases` en modo SSH/Telnet. |
| Requerir propiedad intelectual | En | En modo de punto de acceso, solicite que los clientes tengan una dirección IP. |

Algunas opciones sólo se ofrecen para conexiones SSH/Telnet; `Requerir IP` es específico del modo de punto de acceso. La disponibilidad del sensor depende de lo que informa el enrutador.

## Entities

La integración crea entidades de seguimiento de dispositivos para clientes y sensores para datos de enrutadores compatibles. Los sensores de diagnóstico, como CPU, memoria, temperatura y carga, están desactivados de forma predeterminada donde lo indica Home Assistant; habilite cualquiera de ellos desde la configuración de la entidad. La velocidad de la red, el tráfico y otros valores también pueden estar deshabilitados de forma predeterminada.
## Troubleshooting

- Confirme que Home Assistant pueda comunicarse con el enrutador en el protocolo y puerto seleccionados.
- Verifique el nombre de usuario y la contraseña del enrutador, o que el archivo de clave SSH exista y sea legible por Home Assistant.
- Para configuraciones de puntos de acceso SSH/Telnet, verifique la interfaz seleccionada y la ubicación del archivo de arrendamiento dnsmasq.
- Las entidades de los sensores varían según el modelo de enrutador, el firmware y el protocolo de conexión. Es posible que ese enrutador no proporcione un sensor faltante.
- Los diagnósticos están disponibles en la página del dispositivo de integración. Las credenciales y los datos de identificación seleccionados están redactados.

## Development

Puedo generar el contenido README para este repositorio, pero no puedo escribir directamente en el repositorio porque la cuenta actual no tiene permisos de inserción para `pablogpz/hacore-asuswrt-extended`.

Ya inspeccioné el código y la estructura del repositorio, y este es el archivo README que preparé para ti:

```md
# ASUSWRT (Extended) for Home Assistant

A custom Home Assistant integration for ASUSWRT routers. It discovers devices connected to the router and exposes device trackers and router sensors, with configurable polling and additional device signal-strength (RSSI) information when available.

This integration is a modified version of the ASUSWRT integration in [Home Assistant Core](https://www.home-assistant.io/integrations/asuswrt). It polls the router locally; it does not require a cloud service.

## Features

- Track connected clients with their connection status, hostname, IP address, MAC address, and last-reachable time.
- Expose RSSI for clients when the selected connection method and router provide it.
- Configure the router polling interval (5–300 seconds; default: 30 seconds).
- Provide available router sensors, depending on protocol, model, and firmware:
  - Connected device count, upload/download rates, and traffic totals.
  - CPU usage and per-core usage, memory, uptime, and load averages.
  - Radio and CPU temperatures where supported.
- Choose HTTP, HTTPS, SSH, or Telnet for router communication.
- Configure router or access-point mode for SSH/Telnet connections.

## Installation

This repository is a Home Assistant custom integration. Install its files in the `asuswrt_extended` custom component directory:

```bash
git clone https://github.com/pablogpz/hacore-asuswrt-extended.git \
  /config/custom_components/asuswrt_extended
```

Reemplace `/config` con el directorio de configuración de Home Assistant si es diferente. Luego reinicie Home Assistant y agregue **ASUSWRT (Extendido)** desde **Configuración → Dispositivos y servicios → Agregar integración**.

La integración declara sus requisitos de Python en `manifest.json`; Home Assistant los instala. No se requiere ningún entorno o servicio de Python independiente.

## Configuration

Agregue la integración a través de la interfaz de usuario de Home Assistant y proporcione:

- **Host**: nombre de host o dirección IP del enrutador.
- **Nombre de usuario** y autenticación: contraseña o un archivo de clave SSH para conexiones SSH. La ruta clave debe poder leerse desde el host de Home Assistant.
- **Protocolo**: HTTP, HTTPS, SSH o Telnet. Se puede suministrar un puerto opcional en configuración avanzada.
- **Modo**: para conexiones SSH/Telnet, seleccione el modo enrutador o punto de acceso.

Después de la configuración, use las opciones de integración para configurar:

| Opción | Predeterminado | Descripción |
| --- | --- | --- |
| Intervalo de escaneo del enrutador | 30 segundos | Intervalo de sondeo, configurable de 5 a 300 segundos. |
| Considere su hogar | Rastreador de dispositivos Home Assistant predeterminado | Es hora de esperar antes de marcar un dispositivo perdido. |
| Seguimiento de dispositivos desconocidos | Apagado | Incluya clientes anónimos. |
| Interfaz | `eth0` | Interfaz utilizada para estadísticas en modo SSH/Telnet. |
| dnsmasq alquila ubicación | `/var/lib/misc` | Ubicación de `dnsmasq.leases` en modo SSH/Telnet. |
| Requerir propiedad intelectual | En | En modo de punto de acceso, solicite que los clientes tengan una dirección IP. |

Algunas opciones sólo se ofrecen para conexiones SSH/Telnet; `Requerir IP` es específico del modo de punto de acceso. La disponibilidad del sensor depende de lo que informa el enrutador.
## Entities

La integración crea entidades de seguimiento de dispositivos para clientes y sensores para datos de enrutadores compatibles. Los sensores de diagnóstico, como CPU, memoria, temperatura y carga, están desactivados de forma predeterminada donde lo indica Home Assistant; habilite cualquiera de ellos desde la configuración de la entidad. La velocidad de la red, el tráfico y otros valores también pueden estar deshabilitados de forma predeterminada.
## Troubleshooting

- Confirme que Home Assistant pueda comunicarse con el enrutador en el protocolo y puerto seleccionados.
- Verifique el nombre de usuario y la contraseña del enrutador, o que el archivo de clave SSH exista y sea legible por Home Assistant.
- Para configuraciones de puntos de acceso SSH/Telnet, verifique la interfaz seleccionada y la ubicación del archivo de arrendamiento dnsmasq.
- Las entidades de los sensores varían según el modelo de enrutador, el firmware y el protocolo de conexión. Es posible que ese enrutador no proporcione un sensor faltante.
- Los diagnósticos están disponibles en la página del dispositivo de integración. Las credenciales y los datos de identificación seleccionados están redactados.

## Development

Este repositorio contiene los archivos fuente de integración en su raíz. No define una aplicación independiente ni un comando de prueba; ejecútelo y valídelo en una instancia de Home Assistant con el componente personalizado instalado.
## Credits

Based on the ASUSWRT integration in [home-assistant/core](https://github.com/home-assistant/core/tree/dev/homeassistant/components/asuswrt). See the [Home Assistant ASUSWRT documentation](https://www.home-assistant.io/integrations/asuswrt) for background on the original integration.
```

If you want, I can also produce:
- a shorter, more polished GitHub-style README
- a more technical README for developers
- a version tailored specifically for Home Assistant custom integrations
## Credits

Based on the ASUSWRT integration in [home-assistant/core](https://github.com/home-assistant/core/tree/dev/homeassistant/components/asuswrt). See the [Home Assistant ASUSWRT documentation](https://www.home-assistant.io/integrations/asuswrt) for background on the original integration.
```

If you want, I can also produce:
- a shorter, more polished GitHub-style README
- a more technical README for developers
- a version tailored specifically for Home Assistant custom integrations
