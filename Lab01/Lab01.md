Informe de laboratorio

1. Salida del paso 3 (brokers del clúster).
   
<img width="1073" height="55" alt="image" src="https://github.com/user-attachments/assets/fc14af7b-d7b4-462e-8d2c-4d92597f9abf" />
 
2. Salida del paso 5 (descripción del topic) con el líder de la partición 0 identificado.
   
   <img width="1392" height="88" alt="image" src="https://github.com/user-attachments/assets/bf17dac5-f687-424f-8e4b-65c09b293892" />

3. Salidas del paso 7 antes y después de reiniciar el broker.

   <img width="1407" height="370" alt="image" src="https://github.com/user-attachments/assets/04d0c3ea-92bc-4ca0-89ff-4a2664db3937" />

4. Respuesta a las tres preguntas:
  - P1. ¿Cuántos archivos componen un segmento y para qué sirve cada uno?
    Los archivos del segmento son:

    - **.log:** almacena los mensajes.
    - **.index:** relaciona offsets con posiciones físicas dentro del archivo .log, esto para realizar las búsquedas de una manera rápida.
    - **.timeindex:** para localizar mensajes según la fecha y hora de creación.    
    - **.leader-epoch-checkpoint:** registra cambios de lider.
    - **.partition.metadata:** almacena información de metadatos.
      
  - P2. ¿Qué pasó con el ISR mientras el broker estuvo caído y por qué el clúster siguió aceptando escrituras?
    - Cuando se detuvo el broker líder (2), se eligió automáticamente un nuevo líder. El conjunto ISR disminuyó a dos porque el broker apagado dejó de estar sincronizado. Aunque un broker estuvo apagado, todavía permanecían dos réplicas (1 y 3), y pudo seguir confirmando y almacenando mensajes sin interrumpir el servicio. 
  - P3. ¿Se perdieron mensajes? Explique qué configuración lo garantizó y qué habría pasado con min.insync.replicas=1 y acks=1 si el líder hubiera caído justo después de confirmar una escritura.
    - No se perdieron mensajes. Esto se comprobó al consumir el topic y verificar que se recuperaron los 130 eventos esperados (100 iniciales más 30 enviados durante broker lider apagado).
      La garantía estuvo dada por: replication.factor=3 y min.insync.replicas=2
5. Un párrafo relacionando el ejercicio con un flujo real de su dependencia.
