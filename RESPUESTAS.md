# RESPUESTAS — Reflexión y Resumen (Plantilla genérica)

> **Actividad / ID:**  2-5-Reflexión_Resumen
> **Unidad / Tema:**  Unidad 2
> **Alumno/a:**  Manuel Pérez Romero
> **Fecha:**  23/02/2026

---

## 1) Reflexión crítica (preguntas)

### 1.1) ¿Qué te han parecido los temas tratados en la unidad?
- Me han parecido fundamentales para establecer una base operativa en ciberseguridad. Hemos pasado de la teoría de la taxonomía de incidentes a la implementación práctica de un SOC, lo cual permite entender no solo qué es un ataque, sino cómo se captura y visualiza técnicamente.

### 1.2) ¿Qué ha sido más útil para tu futuro puesto de trabajo? ¿Por qué?
- La implantación y gestión de un SIEM. En un entorno profesional, la capacidad de centralizar logs de distintas fuentes (como Snort y Nginx) es vital para reducir el tiempo de respuesta. Sin un SIEM, el analista está ciego ante eventos correlacionados.

### 1.3) ¿Qué partes ya conocías y cuáles han sido nuevas para ti?
- Conocía conceptos básicos de red, pero han sido totalmente nuevos los Casos de Uso y la evolución de los SIEM hacia capacidades analíticas más avanzadas. También ha sido un descubrimiento la metodología para escribir informes técnicos.

### 1.4) ¿Qué concepto/idea te ha llamado más la atención y por qué?
- El uso de Fuentes Abiertas (OSINT). Me sorprende cómo la inteligencia recolectada de fuentes públicas puede enriquecer las alertas del SIEM para identificar actores de amenazas antes de que el incidente vaya a mas .

### 1.5) ¿Qué parte recortarías o simplificarías si hubiera menos tiempo? Justifica.
- La parte de evolución del SIEM, priorizando más tiempo en la documentación de incidentes, ya que una detección sin un registro técnico adecuado pierde su valor legal y preventivo.

### 1.6) ¿Qué tema has echado en falta o ampliarías? Justifica.
- La parte del post después de haber detectado el ataque por fuerza bruta, para ver la seguridad que se le podría meter 

### 1.7) ¿Qué aplicarías “mañana” en un entorno real con recursos limitados?
- La configuración de un IDS. Como se ve en las evidencias, permite detectar tráfico ICMP y accesos SSH no autorizados de forma inmediata y sin coste de licencia

### 1.8) ¿Qué duda, riesgo o punto crítico te queda abierto tras la unidad?
- El riesgo de los falsos positivos. Si las reglas del SIEM no están bien ajustadas (tuning), el equipo de seguridad puede sufrir fatiga de alertas, ignorando incidentes críticos reales por el exceso de ruido en el dashboard. 


## 2) Resumen esquematizado (obligatorio)

### 2.1) Mapa/índice de la unidad (visión global)

| Punto del Temario | Concepto Fundamental | Aplicación Práctica |
|-------------------|----------------------|---------------------|
| 2.1 Taxonomía | Clasificación estandarizada de incidentes. | Identificar si un ataque es de acceso no autorizado o malware. |
| 2.2 SOC y SIEM | Centros de operaciones y gestión de eventos. | Despliegue del stack ELK para centralizar la vigilancia de la red. |
| 2.3 OSINT | Inteligencia de fuentes abiertas. | Uso de datos públicos para identificar IPs atacantes maliciosas. |
| 2.4 Documentación | Redacción de informes técnicos. | Generación de evidencias y registros tras detectar un incidente. |

### 2.2) Conceptos clave (lista breve)
- **SIEM:** Cerebro central que correlaciona eventos de distintas fuentes.  
- **IDS (Snort):** Sensor que detecta intrusiones mediante firmas de red.  
- **Dashboard:** Panel visual en Kibana para monitorizar alertas en tiempo real.  
- **Normalización:** Proceso de convertir logs variados a un formato común (ECS).

### 2.3) Procesos / procedimientos (pasos o checklist)
- [X] **Instalación:** Despliegue de contenedores Docker (ELK + Agentes).  
- [X] **Configuración:** Definición de reglas en Snort para detectar ICMP y SSH.  
- [X] **Ingesta:** Activación de Filebeat para enviar logs al SIEM.  
- [X] **Monitorización:** Revisión de alertas en el panel *Discover* de Kibana.

### 2.4) Herramientas / técnicas (si aplica)
- **ELK Stack:** Elasticsearch, Logstash y Kibana para el análisis de logs.  
- **Snort:** Motor de detección de intrusiones basado en firmas.  
- **Hydra:** Simulación de ataques de fuerza bruta para validar la detección.  
- **Filebeat:** Agente ligero para el transporte de registros de seguridad.

### 2.5) Buenas prácticas y errores típicos
**Buenas prácticas**
- Sincronizar el tiempo de todos los agentes para evitar desajustes en los logs.  
- Usar el flag `-k none` en Snort para evitar que ignore paquetes en entornos virtuales.

**Errores típicos**
- No aumentar la memoria del sistema (`max_map_count`), impidiendo el arranque del SIEM.  
- Dejar reglas demasiado genéricas que generen miles de falsos positivos.

### 2.6) Glosario mínimo (términos y definiciones cortas)
- **SOC:** Security Operations Center.  
- **Log:** Registro cronológico de eventos de un sistema.  
- **Fuerza Bruta:** Intento masivo de adivinar contraseñas (ej. mediante SSH).  
- **Taxonomía:** Ciencia de la clasificación de incidentes para su correcta gestión.


## 3) (Opcional) Evidencias y recursos usados

### Evidencia 1
**Archivo:** [Captura1.png](evidencias/Captura1.PNG)  
**Qué demuestra:** La recepción de logs en tiempo real. Se observan alertas de prioridad 0 para tráfico ICMP y accesos SSH detectados por el sensor.  
**Qué he aprendido:** A interpretar los campos de un log de Filebeat, identificando IPs de origen (172.19.0.2) y destino (172.19.0.10).

---

### Evidencia 2
**Archivo:** [Captura3.png](evidencias/Captura3.PNG)  
**Qué demuestra:** La efectividad de las reglas del IDS para identificar patrones de ataque (fuerza bruta SSH).  
**Qué he aprendido:** Que el SIEM permite centralizar información de distintos `agent.id` y `agent.hostname` para tener una visión global de la red.


## 4) Conclusión (cierre)
- La Unidad 2 me ha permitido entender que la ciberseguridad no es solo "bloquear", sino "entender" lo que pasa. El dominio de herramientas como ELK y Snort es lo que diferencia a un administrador de sistemas de un analista de seguridad capaz de gestionar un SOC profesional.
