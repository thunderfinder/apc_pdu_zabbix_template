# apc_pdu_zabbix_template

📦 Estructura del Repositorio

apc_pdu_zabbix_template/
├── README.md
├── templates/
│   └── template_apc_pdu.xml
└── mibs/
│    └── powernet457_apc_pdu_check.mib
└── dashboads/
     └── zabbix_apc_pdu_dashboard.json
    

🧩 Contenido del Template
Ítems Monitoreados

El template incluye los siguientes ítems clave:​

    Carga por banco (Amperios): rPDU2BankStatusCurrent

        OID: .1.3.6.1.4.1.318.1.1.26.8.3.1.5

        Unidad: Amperios (A)

    Estado de carga por banco: rPDU2BankStatusLoadState

        OID: .1.3.6.1.4.1.318.1.1.26.8.3.1.4

        Valores posibles: lowLoad, normal, nearOverload, overload

    Estado de carga del dispositivo: rPDU2DeviceStatusLoadState

        OID: .1.3.6.1.4.1.318.1.1.26.4.3.1.4

    Consumo de potencia (kW): rPDU2DeviceStatusPower

        OID: .1.3.6.1.4.1.318.1.1.26.4.3.1.5

        Unidad: kilovatios (kW)

    Energía consumida (kWh): rPDU2DeviceStatusEnergy

        OID: .1.3.6.1.4.1.318.1.1.26.4.3.1.9

        Unidad: kilovatios-hora (kWh)

    Temperatura ambiente: rPDU2SensorTemp

        OID: .1.3.6.1.4.1.318.1.1.26.10.2.3.1.3

        Unidad: grados Celsius (°C)

    Humedad relativa: rPDU2SensorHumidity

        OID: .1.3.6.1.4.1.318.1.1.26.10.2.3.1.4

        Unidad: porcentaje (%)​

Estos OIDs están documentados en las fuentes oficiales de APC.
apc.com
​
Triggers Configurados

Se han establecido triggers con umbrales genéricos basados en recomendaciones del fabricante y expertos en electricidad:​

    Carga por banco > 80%: Alerta de sobrecarga inminente.

    Temperatura ambiente > 35 °C: Riesgo de sobrecalentamiento.

    Humedad relativa > 70%: Posible condensación en el equipo.​

🔐 Configuración de SNMPv3

Para utilizar SNMPv3 en Zabbix, asegúrate de configurar los siguientes parámetros en el host:​

    Versión SNMP: v3

    Nombre de usuario: power

    Nivel de seguridad: authPriv

    Protocolo de autenticación: SHA

    Contraseña de autenticación: powerapc

    Protocolo de privacidad: AES

    Contraseña de privacidad: powerapc​

Estos valores son ejemplos y deben ajustarse según la configuración de tu PDU.
community.se.com
​
📄 Archivo README.md

El archivo README.md incluye:​

    Descripción del template y su propósito.

    Instrucciones para importar el template en Zabbix.

    Guía para configurar SNMPv3 en Zabbix.

    Referencias a la documentación oficial de APC.​

🚀 Próximos Pasos

    Clona o descarga el repositorio desde GitHub.

    Importa el template en Zabbix a través de la interfaz web (Configuration → Templates → Import).

    Asocia el template al host correspondiente 

    Verifica la recolección de datos en Monitoring → Latest data.​



    # Zabbix Template – APC PDU SNMPv3

Este repositorio contiene dos templates para **Zabbix 7** diseñados para monitorear **PDUs APC** mediante **SNMPv3**, basados en el MIB oficial de APC (PowerNet MIB).

## 📦 Contenido

- `template_apc_pdu.xml`: Versión básica con monitoreo de parámetros clave.
- `template_apc_pdu_improved.xml`: Versión mejorada con macros, gráficos, y mapas de valores.

---

## 🚀 Características

### 🧰 Template Básico (`template_apc_pdu.xml`)

Monitorea:

- Corriente por banco (`A`)
- Estado de carga del banco y del dispositivo
- Potencia (`kW`)
- Energía acumulada (`kWh`)
- Temperatura ambiente (`°C`)
- Humedad relativa (`%`)

### 💡 Template Mejorado (`template_apc_pdu_improved.xml`)

Incluye todo lo anterior, más:

- ✅ **Macros configurables**:
  - `{$TEMP_HIGH}` = 35°C
  - `{$HUMIDITY_HIGH}` = 70%
  - `{$LOAD_THRESHOLD}` = 80%
- 📈 **Gráficos prediseñados**:
  - Corriente y potencia
- 🔤 **Mapas de valores** para interpretar el estado de carga:
  - 1 = Bajo
  - 2 = Normal
  - 3 = Cerca de sobrecarga
  - 4 = Sobrecarga

---

## ⚙️ Requisitos

- Zabbix 7.0 o superior
- Acceso SNMPv3 configurado a la PDU APC
- Comunidad SNMP o credenciales v3 (no incluidas por seguridad)

---

## 📥 Importación

1. Accede a Zabbix → **Configuration** → **Templates**
2. Haz clic en **Import**
3. Selecciona uno de los archivos `.xml`
4. Revisa y confirma la importación

---

## 🧠 Recomendaciones

- Asocia este template a hosts que representen tus PDUs APC.
- Ajusta las macros si tus umbrales de operación son diferentes.
- Monitorea las gráficas para observar tendencias y prevenir fallas.

---

## 🔒 Seguridad

Este template está optimizado para **SNMPv3**, que proporciona autenticación y cifrado. Se recomienda evitar SNMPv1 o v2c en entornos de producción.

---

## 🧾 Fuente MIB

Basado en `powernet457_apc_pdu_check.mib` proporcionado por Schneider Electric (APC).

---

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Puedes usarlo, modificarlo y distribuirlo libremente.

---

