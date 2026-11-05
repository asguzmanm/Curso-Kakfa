# **Informe de laboratorio**

**Prerrequisitos**

<img width="921" height="81" alt="image" src="https://github.com/user-attachments/assets/95f12140-4267-438a-84f2-242914c64eeb" /><br>

**1. Paso 1 — Completar el esqueleto**

<img width="921" height="247" alt="image" src="https://github.com/user-attachments/assets/a5a8443e-e6c2-4597-b92f-4a8ae06ba53a" /><br><br>
<img width="921" height="29" alt="image" src="https://github.com/user-attachments/assets/62cf7c8a-778a-4214-bb89-04218ffb4e6f" /><br>

**2. Paso 2 — Rendimiento según acks**

<img width="921" height="48" alt="image" src="https://github.com/user-attachments/assets/0d52100f-53ec-4dab-be44-14b279fa8dc1" /><br>

**3. Paso 3 — Matriz linger.ms × compresión**

<img width="921" height="122" alt="image" src="https://github.com/user-attachments/assets/2b64b89b-1071-4d2c-847e-d720e51c0588" /><br><br>
<img width="921" height="399" alt="image" src="https://github.com/user-attachments/assets/7a95dcbf-3e5c-4da1-9bc4-80e9dd3c2e13" /><br>
 
**4. Paso 4 — Caída del líder durante el envío**

  a. <img width="921" height="91" alt="image" src="https://github.com/user-attachments/assets/b08101cc-56da-485e-ada7-556e7bbf1caa" /><br><br>
  b. <img width="921" height="24" alt="image" src="https://github.com/user-attachments/assets/6a9aab10-18dc-4b55-a565-1a58e16d6e73" /><br><br>
  c. <img width="921" height="41" alt="image" src="https://github.com/user-attachments/assets/e285b2bf-50e8-4ca1-bde2-73dc1d6d1a4e" /><br><br>
  d. <img width="921" height="204" alt="image" src="https://github.com/user-attachments/assets/23e2dada-e8d6-4089-85bc-68fcce77990b" /><br><br>
  e. <img width="921" height="25" alt="image" src="https://github.com/user-attachments/assets/87677a2c-34be-4edc-a463-ff8efaf826e0" /><br>

**Paso 5 — Idempotencia y conteo de duplicados**

  a. <img width="921" height="38" alt="image" src="https://github.com/user-attachments/assets/df94cab5-33da-422f-9efd-4c4ecc96bcda" /><br><br>
  b. <img width="921" height="46" alt="image" src="https://github.com/user-attachments/assets/46295f75-201e-4af8-b24a-048168289be2" /><br><br>
  c. <img width="921" height="40" alt="image" src="https://github.com/user-attachments/assets/578d85d3-bee9-4aec-b702-e81daddb3e29" /><br><br>

**6. Respuesta a:**
 - (a) ¿Qué parámetro habría que cambiar, en qué nivel y con qué herramienta, para que la retención de dian.facturacion.emitida pase a 45 días sin reiniciar?<br>
   - Rta. Se debe cambiar el parámetro retention.ms a nivel de topic usando kafka-configs.sh.
     
 - (b) ¿Por qué la cuota no produce errores en el cliente sino solo lentitud?<br>
   - Rta. Porque Kafka aplica throttling en lugar de rechazar los mensajes, permite que el broker los siga aceptando, pero reduce la tasa de envío para que el cliente no supere la cuota configurada.
     
 - (c) ¿por qué en AWS compartido usamos topics con prefijo por equipo?<br>
   - Rta. Porque todos los equipos trabajan sobre el mismo clúster. Entonces el prefijo permite identificar los topics de cada grupo, evita conflictos e interferencias con los recursos de otro.
