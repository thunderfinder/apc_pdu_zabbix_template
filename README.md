# 🧰 Zabbix Template para PDU APC (SNMPv3)

Este repositorio contiene plantillas listas para usar en Zabbix 7 para monitorear **PDUs de APC** a través de **SNMPv3**, utilizando información del fabricante y buenas prácticas recomendadas por expertos.

---

## 📦 Contenido

- `template_apc_pdu_improved_fixed.xml`: Plantilla sin value maps (usar junto a importación separada de mapas).
- `template_apc_pdu_improved_with_embedded_valuemaps.xml`: Plantilla con value maps integrados.
- `template_apc_pdu_improved_with_embedded_valuemaps_with_triggers_lld_with_prototypes.xml`: Plantilla completa con:
  - Value maps
  - Triggers
  - LLD (descubrimiento automático)
  - Prototipos de ítems y triggers
- `value_map_apc_pdu_load_state.xml`: Mapa de valores "Load State Map" para estados de carga.
- `zabbix_apc_pdu_dashboard.json`: Dashboard para visualización en tiempo real.

---

## 🧠 Triggers y Detección Automática (LLD)

### Triggers Globales

| Nombre                             | Condición                                                    | Severidad |
|------------------------------------|---------------------------------------------------------------|-----------|
| High Temperature                   | Temperatura > `{$TEMP_HIGH}`                                  | High      |
| High Humidity                      | Humedad > `{$HUMIDITY_HIGH}`                                  | Average   |
| Load nearing overload              | Estado de carga = Near Overload (3)                           | Average   |
| PDU Overload                       | Estado de carga = Overload (4)                                | Disaster  |

### Descubrimiento de Bancos (LLD)

La plantilla detecta automáticamente los bancos de carga mediante OID SNMP y crea:

- **Item prototipo:** corriente por banco (Amperios)
- **Trigger prototipo:** alerta si se supera el umbral `{$BANK_LOAD_HIGH}` por banco

### Personalización de Umbrales

Macros definibles por host:

- `{$TEMP_HIGH}` → Temperatura máxima (ej. `40`)
- `{$HUMIDITY_HIGH}` → Humedad máxima (ej. `70`)
- `{$BANK_LOAD_HIGH}` → Corriente máxima por banco (ej. `15`)

---

## 📊 Dashboard

Incluye:

- Honeycombs por estado de PDU
- Gráficos de corriente, carga, temperatura y humedad
- Vista de problemas recientes

Importa `zabbix_apc_pdu_dashboard.json` desde:
```
Zabbix → Dashboards → Import
```

---

## 🚀 Requisitos

- Zabbix 7.0+
- SNMPv3 configurado en el host (ej: IP `192.168.x.x`)
- Modelo APC compatible con MIB PowerNet457

---

## 🛠️ Créditos

Desarrollado a partir de [PowerNet MIB 4.5.7 de APC], documentación de Schneider Electric, y recomendaciones de foros especializados (Reddit, Zabbix, ServerFault).

---

## 📂 Estructura de carpetas

```
apc_pdu_zabbix_template/
├── templates/
│   ├── template_apc_pdu_improved_fixed.xml
│   ├── template_apc_pdu_improved_with_embedded_valuemaps.xml
│   └── template_apc_pdu_improved_with_embedded_valuemaps_with_triggers_lld_with_prototypes.xml
├── value_map_apc_pdu_load_state.xml
├── zabbix_apc_pdu_dashboard.json
└── README.md
```
