# SCADA-Studio5000

Este repositorio reúne los **archivos Ladder (Studio 5000)** desarrollados para distintos retos de **automatización y control industrial**.  
Cada reto incluye su respectiva **simulación en Factory I/O** y, en algunos casos, integración con **Ignition** y **Node-RED**, mostrando aplicaciones de **PLC, SCADA e IoT**.  

Además, cada implementación cuenta con un **video en YouTube** donde se explica el funcionamiento y la lógica aplicada.  

---

## 📂 Retos desarrollados

### 🔹 Reto 1 – Separation Station en Factory I/O
- **Objetivo:** Implementar la escena **Separation Station** de Factory I/O.  
- **Desarrollo:**
  - Creación de toda la lógica de control en **Studio 5000 (Ladder)**.  
  - Configuración de la comunicación entre el PLC y Factory I/O.  
  - Prueba completa de la simulación de separación de piezas.  
- **Resultado:** Un sistema funcional que controla la estación de separación de manera automática.  
- 📺 **Video:** [Ver en YouTube](https://youtu.be/w7zbR262NNk)  

---

### 🔹 Reto 2 – PLC Allen Bradley + IoT (Node-RED)
- **Objetivo:** Integrar un **PLC Allen Bradley** con Factory I/O y conectarlo al **Internet de las Cosas (IoT)**.  
- **Desarrollo:**
  - Programación Ladder en Studio 5000 para controlar la planta simulada en Factory I/O.  
  - Configuración de la comunicación con **Node-RED**, enviando datos del proceso en tiempo real.  
  - Visualización de variables y estados del sistema en dashboards IoT.  
- **Resultado:** Demostración de cómo los PLC industriales pueden conectarse con plataformas IoT para supervisión remota.  
- 📺 **Video:** [Ver en YouTube](https://www.youtube.com/watch?v=eCGR5lQwbcU&list=PLljdzVI2VkAVK_dyDJLEpDmJcOQkOH6A5&index=5)  

---

### 🔹 Reto 3 – Control PID en Factory I/O
- **Objetivo:** Implementar un **control PID en Ladder** para regular un proceso dinámico.  
- **Desarrollo:**
  - Configuración de un lazo de control PID en Studio 5000.  
  - Integración con Factory I/O para simular un sistema físico.  
  - Ajuste de parámetros (ganancias, tiempo integral y derivativo) para lograr estabilidad en el sistema.  
- **Resultado:** Control automático en tiempo real dentro de la simulación, mostrando la efectividad del PID.  
- 📺 **Video:** [Ver en YouTube](https://youtu.be/Ndq8UY__388)  

---

### 🔹 Reto Final – Proceso de manufactura + Gemelo digital + SCADA  
- **Objetivo:** Desarrollar la lógica completa para un proceso de manufactura, construir su gemelo digital en Factory I/O e implementar SCADA en Ignition.  
- **Desarrollo:**
  - Diseño y programación de la **lógica en Ladder (Studio 5000)** para manejar el proceso manufacturero.  
  - Creación del gemelo digital en **Factory I/O**, simulando el sistema real con todos sus componentes y comportamiento.  
  - Implementación de un proyecto SCADA en **Ignition**, conectando variables del proceso con interfaces gráficas, alarmas, control y monitoreo.  
- **Resultado:** Una solución integral que va desde la lógica de control hasta la visualización SCADA, pasando por la simulación realista del sistema.  
- 📺 **Video:** [Ver en YouTube](https://www.youtube.com/watch?v=YjniLJiRvuo&list=PLljdzVI2VkAUmnLpZfumW2bdHxuZ3lAqO&index=4)  

---

## ⚙️ Tecnologías utilizadas
- **Studio 5000 (Allen Bradley / Rockwell Automation)** → Programación Ladder.  
- **Factory I/O** → Simulación de procesos industriales.  
- **Node-RED** → Integración con IoT y dashboards.  
- **Ignition** → Supervisión y control SCADA (en algunos proyectos).  
