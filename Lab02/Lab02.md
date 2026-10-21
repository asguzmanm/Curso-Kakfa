# **Informe de laboratorio**

**1. Salida del paso 2 con LeaderId y LeaderEpoch.**

 <img width="1494" height="169" alt="image" src="https://github.com/user-attachments/assets/1341a325-ae1f-4080-bb3a-b957914e3dfa" /><br><br>
 <img width="878" height="85" alt="image" src="https://github.com/user-attachments/assets/392cd814-5504-4026-84f4-2b556e250cd7" /> <br>

**2. Registros del paso 4 (TOPIC_RECORD y un PARTITION_RECORD).**

 <img width="1496" height="255" alt="image" src="https://github.com/user-attachments/assets/388aaef1-abb9-424f-b2e8-a1d05845a948" /><br>

**3. Salidas del paso 5 antes y después de la caída, con el tiempo de elección medido, y la respuesta a la pregunta de los dos nodos.**

 <img width="1495" height="648" alt="image" src="https://github.com/user-attachments/assets/7c6aa5d5-3b25-48d9-8c78-e24b6a92c581" /><br><br>
 **¿Qué habría pasado si hubiera detenido dos de los tres nodos?**: el clúster habría perdido el quórum, para tres "votantes" se requiere una mayoría de dos nodos para mantener el liderazgo y confirmar cambios, con solo un nodo disponible no sería posible elegir controlador ni realizar operaciones sobre el clúster.

**4. Salida del paso 6 con particiones y offsets, y la del grupo ${EQUIPO}-lab02-lector.**

<img width="1497" height="341" alt="image" src="https://github.com/user-attachments/assets/562b6c4b-d192-468b-83cc-68f3b122e6a9" /><br>

**5. El diagrama del paso 7.**

<img width="3424" height="1045" alt="image" src="https://github.com/user-attachments/assets/ac082171-fd59-4b73-8f44-d1ef4f7ebfb3" />

**6. Un párrafo: ¿por qué KRaft simplifica la operación frente a ZooKeeper en una entidad como la DIAN?**

KRaft simplifica la operación porque elimina la dependencia de ZooKeeper, concentrando la gestión de metadatos directamente en el clúster Kafka, haciendo que la administración sea más sencilla, con menos componentes que monitorear y menos posibilidades de falla.
