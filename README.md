# SCADA-Studio5000

This repository brings together **Ladder (Studio 5000) files** developed for different challenges in **automation and industrial control**.  
Each challenge includes its corresponding **simulation in Factory I/O**, and in some cases, integration with **Ignition** and **Node-RED**, showcasing applications of **PLC, SCADA, and IoT**.  

Each implementation is also accompanied by a **YouTube video** explaining its operation and the applied logic.  

---

## 📂 Developed Challenges

### 🔹 Challenge 1 – Separation Station in Factory I/O
- **Goal:** Implement the **Separation Station** scene in Factory I/O.  
- **Development:**
  - Full control logic created in **Studio 5000 (Ladder)**.  
  - Configuration of communication between the PLC and Factory I/O.  
  - Complete testing of the part-separation simulation.  
- **Result:** A functional system that automatically controls the separation station.  
- 📺 **Video:** [Watch on YouTube](https://youtu.be/w7zbR262NNk)  

---

### 🔹 Challenge 2 – Allen Bradley PLC + IoT (Node-RED)
- **Goal:** Integrate an **Allen Bradley PLC** with Factory I/O and connect it to the **Internet of Things (IoT)**.  
- **Development:**
  - Ladder programming in Studio 5000 to control the simulated plant in Factory I/O.  
  - Setup of communication with **Node-RED**, sending real-time process data.  
  - Visualization of system variables and states through IoT dashboards.  
- **Result:** Demonstrates how industrial PLCs can be connected to IoT platforms for remote monitoring.  
- 📺 **Video:** [Watch on YouTube](https://www.youtube.com/watch?v=eCGR5lQwbcU&list=PLljdzVI2VkAVK_dyDJLEpDmJcOQkOH6A5&index=5)  

---

### 🔹 Challenge 3 – PID Control in Factory I/O
- **Goal:** Implement a **PID control in Ladder** to regulate a dynamic process.  
- **Development:**
  - Configuration of a PID control loop in Studio 5000.  
  - Integration with Factory I/O to simulate a physical system.  
  - Parameter tuning (proportional, integral, and derivative gains) to achieve system stability.  
- **Result:** Automatic real-time control within the simulation, demonstrating the effectiveness of PID.  
- 📺 **Video:** [Watch on YouTube](https://youtu.be/Ndq8UY__388)  

---

### 🔹 Final Challenge – Manufacturing Process + Digital Twin + SCADA  
- **Goal:** Develop the full control logic for a manufacturing process, build its digital twin in Factory I/O, and implement SCADA in Ignition.  
- **Development:**
  - Design and programming of the **Ladder logic (Studio 5000)** to manage the manufacturing process.  
  - Creation of the digital twin in **Factory I/O**, simulating the real system with all its components and behavior.  
  - Implementation of a SCADA project in **Ignition**, connecting process variables with graphical interfaces, alarms, control, and monitoring.  
- **Result:** A comprehensive solution covering control logic, realistic simulation, and SCADA visualization.  
- 📺 **Video:** [Watch on YouTube](https://www.youtube.com/watch?v=YjniLJiRvuo&list=PLljdzVI2VkAUmnLpZfumW2bdHxuZ3lAqO&index=4)  

---

## ⚙️ Technologies Used
- **Studio 5000 (Allen Bradley / Rockwell Automation)** → Ladder programming  
- **Factory I/O** → Industrial process simulation / digital twin  
- **Node-RED** → IoT integration and dashboards  
- **Ignition** → SCADA for monitoring and control (in some projects)  
