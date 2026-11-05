# **Informe de laboratorio**

**Prerrequisitos**

<img width="921" height="303" alt="image" src="https://github.com/user-attachments/assets/21c98b86-2421-4a6e-849a-409cf2e49caa" /><br>

**1. Paso 1 — Consumidor con commit manual**

<img width="921" height="275" alt="image" src="https://github.com/user-attachments/assets/30421232-7ecd-4502-bafb-03623cce105a" /><br><br>
Al ejecutar el comando, se presentó error, se ajusta el puerto y se solventa:<br><br>
<img width="921" height="102" alt="image" src="https://github.com/user-attachments/assets/c302e571-b9be-42fd-a29b-b21149f42070" /><br>

**2. Paso 2 — Caída entre el INSERT y el commit**

<img width="921" height="138" alt="image" src="https://github.com/user-attachments/assets/9588f7d1-3d83-4101-8ed7-fcc4625593cd" /><br><br>
<img width="921" height="210" alt="image" src="https://github.com/user-attachments/assets/13f6e420-7e80-4e76-b7b0-67550bba4ed5" /><br>

**3. Paso 3 — Idempotencia con UPSERT**

<img width="921" height="283" alt="image" src="https://github.com/user-attachments/assets/3eac6042-8621-4bde-b995-e2a56b0ead19" /><br>
 
**4. Paso 4 — Reposicionar el grupo a una marca de tiempo**

<img width="921" height="217" alt="image" src="https://github.com/user-attachments/assets/01a19422-64e7-4d64-a9e6-e1f822c20c36" /><br>

**5. Paso 5 — Mensaje malformado**

<img width="921" height="116" alt="image" src="https://github.com/user-attachments/assets/0cc70bc0-94db-4bb1-a3b6-21cea1468c98" /><br>

**6. Paso 6 — Inspeccionar la DLQ**

<img width="921" height="78" alt="image" src="https://github.com/user-attachments/assets/1b684581-2274-4f63-b57c-0eeb1ea62d75" /><br>

**7. Respuesta a:**
 - (a) explique con sus palabras por qué el paso 2 falló y el 3 no
   - Rta. El paso 2 falló porque el mensaje sí se alcanzó a guardar en la base de datos, pero el consumidor se cayó antes de confirmar el offset en Kafka. Cuando volvió a arrancar, Kafka entregó nuevamente ese mensaje y se intentó insertar otra vez el mismo id_evento, generando el error de clave primaria duplicada. En el paso 3 no ocurrió porque se utilizó UPSERT, por lo que al reprocesar el mensaje simplemente se actualizó o ignoró el registro existente sin generar duplicados.
     
 - (b) ¿en qué caso preferiría "guardar el offset en el destino" en lugar del UPSERT?
   -  Rta. Preferiría guardar el offset en el destino cuando necesito que la escritura del dato y el avance del offset queden en una misma transacción. Así, si se confirma el offset, tengo garantía de que el dato quedó almacenado, evitando reprocesos.
     
 - (c) quién debería ser el responsable de la DLQ del flujo de facturación en la entidad y qué acuerdo de atención propondría.
   - Rta.  El responsable de la DLQ debería ser el equipo funcional o de soporte encargado de la facturación electrónica dentro de la entidad, ya que son quienes pueden validar y corregir los documentos rechazados. Como acuerdo de atención propondría revisar la DLQ diariamente, atender errores críticos en menos de 4 horas hábiles y resolver los demás casos en máximo 1 día hábil.
