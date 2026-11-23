<img width="921" height="156" alt="image" src="https://github.com/user-attachments/assets/d2221277-1ee8-4e7f-99a4-5763fee99554" /># **Informe de laboratorio**

**Prerrequisitos**

<img width="921" height="49" alt="image" src="https://github.com/user-attachments/assets/9a052df2-f4a3-4d0e-88ea-662a5cc0cedc" /><br>

**1. Paso 1 — Producción continua**

<img width="921" height="29" alt="image" src="https://github.com/user-attachments/assets/cc961c39-6d2c-42bf-9209-f83c5c348a0d" /><br><br>
El productor inicia la generación de 500 registros por minuto durante 12 minutos<br>

**2. Paso 2 — Un consumidor; medir el lag cada 30 s**

<img width="921" height="50" alt="image" src="https://github.com/user-attachments/assets/08981bcb-b414-45ae-b9ce-8025b7bbabe7" /><br><br>
<img width="921" height="57" alt="image" src="https://github.com/user-attachments/assets/23ca206a-453b-4592-88f1-c521fc204d67" /><br><br>
Consumidor:<br>
<img width="921" height="149" alt="image" src="https://github.com/user-attachments/assets/9aaf5a98-4367-4604-8704-e8480077c996" /><br>

**3. Paso 3 — Escalar a 3 y a 6**

<img width="921" height="42" alt="image" src="https://github.com/user-attachments/assets/fb0e0af9-9ae7-4dab-95e0-1c61b79d6850" /><br><br>
<img width="921" height="102" alt="image" src="https://github.com/user-attachments/assets/266f6a3a-1649-46b1-bb8a-19774365e22e" /><br><br>

Cambian los lags, dejan de crecer y empiezan a bajar lentamente. Se cambia a 6 consumidores: <br>

<img width="921" height="162" alt="image" src="https://github.com/user-attachments/assets/8777aa0c-4868-4b7c-a6a4-945ca07372fe" /><br><br>
<img width="921" height="106" alt="image" src="https://github.com/user-attachments/assets/d6cb9709-dc4e-4374-878d-548b8d9d1192" /><br>
 
**4. Paso 4 — Séptimo consumidor**

<img width="921" height="156" alt="image" src="https://github.com/user-attachments/assets/c8814ee1-5611-4d6e-9c1a-0830d5332f57" /><br><br>
<img width="921" height="137" alt="image" src="https://github.com/user-attachments/assets/c10ac16e-9d27-4a32-97a5-2741dba2ffda" /><br>

**5. Paso 5 — Eager vs. cooperativo**

<img width="921" height="71" alt="image" src="https://github.com/user-attachments/assets/fd3854ec-ef99-4801-aa4e-98fc95e82574" /><br>

**6. Paso 6 — Ciclo de expulsión por poll lento**

<img width="921" height="73" alt="image" src="https://github.com/user-attachments/assets/313f7ad8-acf7-4f0d-95e3-f75c760f493e" /><br>

**7. Respuesta a:**
 - Relación con un flujo de su dependencia: ¿cuántas particiones y consumidores propondría y qué umbral de lag alertaría?
   - Rta. 
