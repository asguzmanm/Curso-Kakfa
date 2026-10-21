# **Informe de laboratorio**

**1. Salida del paso 3 (brokers del clúster).**
   
<img width="1073" height="55" alt="image" src="https://github.com/user-attachments/assets/fc14af7b-d7b4-462e-8d2c-4d92597f9abf" />
 
**2. Salida del paso 5 (descripción del topic) con el líder de la partición 0 identificado.**
   
   <img width="1392" height="88" alt="image" src="https://github.com/user-attachments/assets/bf17dac5-f687-424f-8e4b-65c09b293892" />

**3. Salidas del paso 7 antes y después de reiniciar el broker.**

   <img width="1407" height="370" alt="image" src="https://github.com/user-attachments/assets/04d0c3ea-92bc-4ca0-89ff-4a2664db3937" />

**4. Respuesta a las tres preguntas:**

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
    - No se perdieron mensajes. Esto se verifico al consultar el topic y validar que se encuentran los 130 registros esperados (100 iniciales más 30 enviados mientras el broker lider estaba detenido). Y lo que garantizo lo anterior fue la configuración replication.factor=3 y min.insync.replicas=2 que obligan a que al menos dos réplicas mantengan una copia de los datos.
    - Si la configuración hubiera sido min.insync.replicas=1 y acks=1, el líder habría podido confirmar la recepción del mensaje, sin esperar a que las réplicas lo copiaran, pero si el líder hubiera fallado (después de la confirmación y antes de replicar el registro) el mensaje podría haberse perdido porque no habría otra réplica actualizada.
      
**5. Un párrafo relacionando el ejercicio con un flujo real de su dependencia.**

- Este ejercicio puede relacionarse con el proceso de recepción de declaraciones tributarias. Cuando un contribuyente presenta una declaración, el evento puede publicarse en un topic de Kafka. La replicación entre brokers garantiza que la información no se pierda ante la caída de un servidor, mientras que el ISR asegura que existan varias copias sincronizadas antes de confirmar la recepción del evento. Para que procesos posteriores puedan consumir los eventos de manera confiable, manteniendo la disponibilidad y la integridad de la información tributaria.
