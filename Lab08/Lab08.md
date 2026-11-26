# **Informe de laboratorio**

**Prerrequisitos**

<img width="921" height="63" alt="image" src="https://github.com/user-attachments/assets/df0ef477-f1d8-4b77-8a6b-34e9ddd4b1e0" /><br><br>
<img width="921" height="49" alt="image" src="https://github.com/user-attachments/assets/e794c962-89d0-4527-9b3b-4273158ed10e" /><br>

**1. Paso 1 — Revisar el esquema**

<img width="921" height="188" alt="image" src="https://github.com/user-attachments/assets/dac96469-b12e-46cb-b04b-f6bd2d76f2c3" /><br>

**2. Paso 2 — Registrar el esquema**

Muestra el registro, formato y paquete del esquema:<br><br>
<img width="921" height="44" alt="image" src="https://github.com/user-attachments/assets/fab3c2e8-3356-462a-9ef0-18f465b0e16c" /><br><br>
<img width="921" height="33" alt="image" src="https://github.com/user-attachments/assets/9f9a2fa6-e54e-4b2e-bafd-37050192e2ef" /><br><br>
Se cambia curl -s http://localhost:8081/config/dian.declaracion.presentada-value:<br><br>
<img width="921" height="30" alt="image" src="https://github.com/user-attachments/assets/84377317-dfbe-440d-8ee3-e34bff47b891" /><br>

**3. Paso 3 — Producir y consumir con Avro**

<img width="921" height="145" alt="image" src="https://github.com/user-attachments/assets/5931e93c-1c3d-49ed-a1e9-e88a5934e70f" /><br>
 
**4. Paso 4 — El mensaje en crudo**

<img width="921" height="90" alt="image" src="https://github.com/user-attachments/assets/7c46026a-d19b-4638-9d1a-60e940124d8b" /><br><br>
Después de los dos punto y coma (:), los dos primeros 0s se considera byte mágico, lo siguientes 4 hasta el 0 antes del 1, es el ID del esquema, y lo demás es la declaración en avro que esta en binario. Así mismo los que están en un formato tipo letras y números son el nit, como se tiene el esquema, se sabe que valores son los que se leen.<br>

**5. Paso 5 — Un evento que viola el esquema**

<img width="921" height="54" alt="image" src="https://github.com/user-attachments/assets/708820e5-bb2d-43ab-8eb6-b9868f5b686c" /><br><br>
Se esta enviando el nuevo productor con 5, pero con un valor En Tramite, y como este último no esta definido en la lista de los estados, aparece 0 enviados y lo detiene el serializador.<br>

**6. Paso 6 — Consultar el esquema por ID**

<img width="921" height="84" alt="image" src="https://github.com/user-attachments/assets/243d0eb8-c2d3-4b82-9605-f8aa9c2f293d" /><br><br>
<img width="921" height="591" alt="image" src="https://github.com/user-attachments/assets/a29e9f8b-324f-434f-a72c-15bfbd48b483" /><br>

**7. Respuesta a:**
 - (a) ¿qué impide el enum?
   - Rta. Impide que se envíen valores diferentes a los definidos en el esquema, evitando errores de escritura o estados no válidos.
 - (b) ¿por qué solo viaja el ID?
   - Rta. Porque enviar el esquema completo en cada mensaje aumentaría innecesariamente su tamaño. Con el ID, el consumidor puede consultar el esquema en Schema Registry cuando lo necesite.
 - (c) ¿qué habría pasado en la sesión 7, con JSON sin esquema, al producir EN_TRAMITE?
   - Rta. El mensaje probablemente se habría enviado sin problemas, ya que no existía una validación que controlara los valores permitidos para ese campo.
 - (d) proponga dos campos que agregaría al esquema para su propio dominio y redacte su doc
   - Rta. 
     - cod_dependencia: Código de la dependencia responsable de generar o procesar el evento.
     - usuario_proceso: Identificador del usuario o proceso que realizó la última acción sobre el registro.

