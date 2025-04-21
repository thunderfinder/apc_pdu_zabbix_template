
# APC PDU Zabbix Template for EPDU1116M

This repository provides a complete Zabbix 7 template for monitoring **APC EPDU1116M** power distribution units (PDUs) using SNMPv3.

---

## 📦 Included

- YAML Template compatible with **Zabbix 7.0**
- Preconfigured **items**, **triggers**, **macros**, **LLD rules**, and **value mappings**
- Dynamic discovery of PDU **outlets**
- Dashboard JSON for visual monitoring in Zabbix UI
- Thresholds aligned with **APC manufacturer specs**

---

## 📥 Installation (English)

1. Import the template:
   - Go to `Configuration → Templates → Import`
   - Upload `template_apc_epdu1116m_fixed_expression.yaml`

2. Import the dashboard:
   - Go to `Monitoring → Dashboards → Import`
   - Upload `dashboard_epdu1116m_fixed.json`

3. Assign the template to your PDU host configured with SNMPv3.

4. Set required macros:
   - `{$SNMP_COMMUNITY}`
   - `{$PDU_MAX_CURRENT}` – default: `16`
   - `{$OUTLET_MAX_CURRENT}` – default: `10`

---

## 📥 Instalación (Español)

1. Importa la plantilla:
   - Ve a `Configuración → Plantillas → Importar`
   - Sube el archivo `template_apc_epdu1116m_fixed_expression.yaml`

2. Importa el dashboard:
   - Ve a `Monitoreo → Dashboards → Importar`
   - Sube el archivo `dashboard_epdu1116m_fixed.json`

3. Asigna la plantilla al host de tu PDU con SNMPv3.

4. Configura las macros necesarias:
   - `{$SNMP_COMMUNITY}`
   - `{$PDU_MAX_CURRENT}` – por defecto: `16`
   - `{$OUTLET_MAX_CURRENT}` – por defecto: `10`

---

## 📊 Dashboard

![Zabbix Dashboard](https://raw.githubusercontent.com/thunderfinder/apc_pdu_zabbix_template/main/img/dashboard_preview.png)

The dashboard includes:
- Active problems
- Graphs for voltage, load, humidity, temperature
- Energy stats
- Clock widget

---

## 🧠 Triggers Highlights

| Name | Description | Priority |
|------|-------------|----------|
| Overvoltage | Voltage > 253V or < 207V | High |
| High Temperature | Temp > 45°C | Disaster |
| Load > 80% | Warns on high consumption | Warning |
| Outlet State Change | Detects ON/OFF changes | Info |

---

## 📚 Sources

- APC EPDU1116M Specs Sheet
- Schneider Electric SNMP Reference Guide
- PowerNet MIB v4.5.7

---

## 👨‍💻 Author

DEVELOPED by [@abaldakin](https://github.com/zabbix/community-templates/blob/main/Power_(UPS)/APC/template_apc_pdu_new_snmp/6.0/template_apc_pdu_new_snmp.yaml)

MODDED by [@thunderfinder](https://github.com/thunderfinder) + CHATGPT MODEL 4o

Feel free to contribute or open an issue if you find improvements.

