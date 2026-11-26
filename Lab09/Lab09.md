# **Informe de laboratorio**

**Prerrequisitos**

<img width="921" height="62" alt="image" src="https://github.com/user-attachments/assets/89cac8d5-f22b-4a36-98a6-264f7133fdce" /><br>

**1. Paso 1 — Source JDBC incremental**

<img width="921" height="59" alt="image" src="https://github.com/user-attachments/assets/bed90d04-07dd-4e0b-9aa0-ab7681cac806" /><br><br>
<img width="921" height="308" alt="image" src="https://github.com/user-attachments/assets/1405a3f1-db14-43a6-9c50-d351c7149371" /><br>

**2. Paso 2 — Verificar el esquema derivado automáticamente**

Muestra el registro, formato y paquete del esquema:<br><br>
<img width="921" height="83" alt="image" src="https://github.com/user-attachments/assets/08bbcdd5-1163-4d47-9af6-5c52fa6b2aae" /><br><br>
<img width="921" height="74" alt="image" src="https://github.com/user-attachments/assets/0eece820-3da2-436d-853d-1748bf6884a4" /><br><br>
Se observa el esquema derivado<br>

**3. Paso 3 — Efecto de las SMT**

<img width="921" height="104" alt="image" src="https://github.com/user-attachments/assets/f0a8026b-4426-4aa6-b2db-75a7673d06a7" /><br><br>
¿Qué implicación de cumplimiento tiene enmascarar en tránsito antes de que el dato llegue al destino analítico?: El dato sensible se enmascara antes de ser consumido por las plataformas analíticas, evitando que estas accedan al valor real. De esta manera se reduce el riesgo de exposición de información identificable y se fortalecen los controles de protección de datos.<br>
 
**4. Paso 4 — Sink hacia MinIO**

<img width="921" height="115" alt="image" src="https://github.com/user-attachments/assets/b5f1cc80-4fd3-4c51-b892-d33dc5dc0669" /><br><br>

**5. Paso 5 — JDBC frente a CDC**

<img width="921" height="37" alt="image" src="https://github.com/user-attachments/assets/8b0be3ce-f67a-4cdf-85a6-5cbdbf7c12e6" /><br><br>
<img width="921" height="46" alt="image" src="https://github.com/user-attachments/assets/910eb281-909c-4dd9-b9ba-23a1bb138921" /><br>

**6. Paso 6 — Redistribución de tareas**

<img width="921" height="150" alt="image" src="https://github.com/user-attachments/assets/bcf99b60-6aff-40b5-81c5-9d6e604e885c" /><br>

**7. Respuesta a:**

Tabla comparativa:

| Dimensión | JDBC incremental | CDC (Debezium) |
|------------|------------------|----------------|
| Latencia observada | Algunos segundos. | Casi que inmediato. |
| ¿Detectó el DELETE? | No detecta. | Sí detecta. |
| Carga sobre el origen | Carga Media. | Carga Baja. |
| Requisitos previos | Acceso JDBC y una columna para identificar cambios. | Replicación lógica habilitada. |

a) Implicación de cumplimiento del enmascaramiento en tránsito
 - Rta. El dato sensible se enmascara antes de llegar a los sistemas analíticos, evitando que los usuarios accedan al dato real. Esto reduce el riesgo de exposición de información sensible y fortalece los controles de privacidad y confidencialidad.

b) ¿Qué área de la DIAN debe autorizar los permisos de replicación y qué le argumentaría?
 - Rta. El permiso debería ser aprobado por los administradores de bases de datos y seguridad de la información. Les argumentaría que Debezium permite capturar cambios en tiempo real con menor impacto sobre las tablas productivas y con mayor trazabilidad de los datos.

(c) Flujo de su dependencia donde usaría CDC y por qué
 - Rta. Utilizaría CDC para el seguimiento de solicitudes y correcciones de declaraciones. De esta manera, los cambios se reflejarían en tiempo real en los sistemas analíticos, facilitando el monitoreo y la trazabilidad de las modificaciones.
