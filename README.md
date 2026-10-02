<!-- HEADER BANNER -->
<div align="center">
  <img src="./assets/banner-binario.jpg" width="100%" alt="Cybersecurity & Binary Code Banner" />
</div>

<br />

<!-- HEADER WITH UNALM SHIELD -->
<table border="0" width="100%">
  <tr>
    <td width="78%" valign="top">
      <h1>🔍 Statistical Threat Detection & Unsupervised SIEM Platform</h1>
      <h3>Enterprise Multi-Source Telemetry Normalizer, Unsupervised Anomaly Engine & Real-Time Monitoring SIEM</h3>
      <p>
        👤 <b>Autor:</b> Brian Alva Aquino (<a href="https://github.com/blolchevere-ctrl">@blolchevere-ctrl</a>)<br />
        🎓 <b>Institución:</b> Universidad Nacional Agraria La Molina (UNALM)<br />
        📚 <b>Área:</b> SIEM Architecture, Unsupervised ML & Threat Intelligence
      </p>
      <p>
        <img src="https://img.shields.io/badge/System-SIEM_Engine-00599C?style=flat-square&logo=splunkelementary" alt="SIEM" />
        <img src="https://img.shields.io/badge/ML-Isolation_Forest-orange?style=flat-square" alt="Isolation Forest" />
        <img src="https://img.shields.io/badge/Analytics-Time_Series-green?style=flat-square" alt="Time Series" />
        <img src="https://img.shields.io/badge/Status-Production_Ready-brightgreen?style=flat-square" alt="Status" />
      </p>
    </td>
    <td width="22%" align="center" valign="middle">
      <img src="./assets/escudo-unalm.png" width="120" alt="Escudo UNALM" />
    </td>
  </tr>
</table>

---

## 📌 Arquitectura General del Sistema

Este repositorio alberga un **sistema SIEM (Security Information and Event Management) unificado** diseñado para la correlación cross-platform de eventos de seguridad provenientes de servidores Linux y gestores de bases de datos SQL.

Mediante técnicas de **aprendizaje automático no supervisado** y **análisis de series temporales**, la plataforma detecta comportamientos anómalos o amenazas "Zero-Day" sin necesidad de contar con firmas o etiquetas previas.

---

## ⚙️ Componentes de la Solución

```text
  [ Syslogs Linux ] ──┐
                      ├──► ┌────────────────────────┐      ┌─────────────────────────┐      ┌────────────────────────┐
  [ SQL Audit Logs ] ─┘    │ 1. ETL y Estandarizado │ ───► │ 2. Detección No Superv. │ ───► │ 3. Dashboard & Alerts  │
                           └────────────────────────┘      └─────────────────────────┘      └────────────────────────┘
```

### 1. Engine de Ingesta y Estandarización Multi-Fuente
* **ETL Pipeline:** Recolección unificada de trazas heterogéneas desde servidores Linux (Syslog, Auth) y motores SQL (PostgreSQL Audit, MySQL General Log).
* **Esquema Común de Eventos:** Normalización de logs en estructuras JSON con metadatos estandarizados (`timestamp`, `source_ip`, `user_entity`, `event_type`, `severity_score`).

### 2. Motor de Detección No Supervisada de Anomalías
* **Machine Learning no Supervisado:** Aplicación de **Isolation Forest** y **Autoencoders** para la identificación de desviaciones en el comportamiento habitual del sistema.
* **Series Temporales:** Detección de picos inusuales en el volumen de consultas o conexiones mediante análisis de componentes estacionales y medias móviles ponderadas.

### 3. Centro de Control, Dashboard e Interfaz SIEM
* **Dashboard Interactivo:** Panel de monitoreo en tiempo real desarrollado en Streamlit / Dash.
* **Visualización de Amenazas:** Mapas de calor de actividad hostil, histogramas de distribución de anomalías y seguimiento de métricas clave.
* **Sistema de Alerta:** Emisión de notificaciones automáticas ante eventos con *Anomaly Score* superior al umbral crítico definido.

---

## 📂 Estructura del Repositorio

```text
Statistical-Threat-Detection-and-Anomaly-SIEM-for-Linux-and-SQL/
├── assets/
│   ├── banner-binario.jpg
│   └── escudo-unalm.png
├── config/
│   └── siem_config.yaml
├── data/
│   ├── raw_logs/              # Syslogs y registros SQL brutos
│   └── processed/             # Eventos JSON estandarizados
├── src/
│   ├── __init__.py
│   ├── ingest_pipeline.py     # ETL y normalización multi-fuente
│   ├── anomaly_detector.py    # Isolation Forest y Series Temporales
│   └── alert_system.py        # Gestor de reglas y alertas
├── dashboard/
│   └── app.py                 # Interfaz gráfica SIEM en Streamlit
├── notebooks/
│   └── anomaly_eval.ipynb
├── tests/
│   └── test_siem.py
├── requirements.txt
└── README.md
```
