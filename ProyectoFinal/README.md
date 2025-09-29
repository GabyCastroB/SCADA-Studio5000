# Final Project — Manufacturing Line (Digital Twin + Ladder Logic + SCADA)

**Video demo:** https://www.youtube.com/watch?v=YjniLJiRvuo&list=PLljdzVI2VkAUmnLpZfumW2bdHxuZ3lAqO&index=5

This folder contains the files, configuration and documentation for the final project of the SCADA / Industrial Controllers course.  
The project implements a small manufacturing line with:

- A **three-level elevator** that selects different products per floor.
- **Factory I/O** digital twin (custom scene).
- **Ladder logic** programmed in **Studio 5000** (CompactLogix).
- **SCADA** visualization and control in **Ignition**.
- **Node-RED** + **Python API (Flask)** for autonomy / market-driven production (uses Google Trends data).
- Physical I/O mapping for a demo bench (motors and pneumatic actuators).

![FactoryIO Digital twin](https://github.com/GabyCastroB/SCADA-Studio5000/blob/main/Images/FactoryIO.png)
---

## Quick project overview

The line simulates a small packaging/assembly process:

1. A conveyor brings an empty basket to the elevator.
2. The elevator moves to a selected floor (1, 2 or 3). Each floor corresponds to a different product type.
3. The elevator loads **3 products per basket** (one per inner sensor) and returns to the assembly station.
4. A pneumatic/robotic arm takes the items and places them on a pallet. Each pallet requires **6 final items** (two full baskets).
5. Production orders can be issued manually from Ignition (supervisor login) or automatically via a Market-Demand API processed by Node-RED.
6. The PLC (CompactLogix) controls the sequence and communicates with Factory I/O (digital twin) and Ignition through OPC / Ethernet/IP.

---

## How the ladder logic is organized (Studio 5000)

Main ideas and how the program is structured — this mirrors the implementation shown in the video:

### Main routine
- Supervises high-level states: `IDLE`, `LOAD`, `MOVE_ELEVATOR`, `UNLOAD`, `ASSEMBLE`, `PALET_COMPLETE`.
- Receives orders (manual from Ignition or automatic from Node-RED).
- Prevents new order acceptance until the previous order finishes (ensures two baskets per pallet).

### Subroutines / UDTs used
- **Subroutine: `SENSOR_SELECTOR`**  
  Dynamically maps `sensor_low` and `sensor_high` according to the selected floor. This avoids duplicating code for each floor.

- **Subroutine: `ELEVATOR_CONTROL`**  
  Uses variables:
    - `piso_producto` (product floor)
    - `piso_destination` (destination floor; 0 = down)
    - `sensor_low` / `sensor_high` — bottom & top sensors for the current floor  
      Controls elevator motor direction and stopping using the selected sensors.

- **Subroutine: `PRODUCT_COUNTERS`**  
  Counts items per basket and per pallet; increments the assembly counter when an assembly action is completed.

- **Tag naming (recommended)**
    - `Product_Select` — integer tag (1..3) set by Ignition or Node-RED
    - `Order_Request` — BOOL set when a new production order arrives
    - `Elevator_Floor` — INT (0..3) current elevator floor
    - `Basket_Count` / `Pallet_Count` — INT counters
    - `Sensor_FloorX_Low` / `Sensor_FloorX_High` — Discrete inputs

### Key control logic patterns
- **Dynamic sensor mapping:** depending on `piso_producto`, the program points `sensor_low`/`sensor_high` variables to the corresponding physical tags and uses the same code paths.
- **Order precedence:** Manual SCADA selection has priority over automatic requests, but the PLC will not accept a new request until the previous one completes (to guarantee the pallet completes).
- **Movement direction decision:** `if piso_destination > piso_current → move up; if piso_destination < piso_current → move down; if equal → stop`. Destination `0` means go to ground (down).

---

## Node-RED + Market-Demand API (Autonomy feature)

### Purpose
Automatically choose which product to prioritize according to market demand (demonstrates a basic autonomous production adaptation).

### Flow summary
1. **Inject node** triggers periodic HTTP GET to the Flask API.
2. **HTTP Request node** calls the Google Trends API endpoint (Flask app).
3. **Function node** parses the JSON and extracts the product ID (e.g. `1 = Pilsen`, `2 = Águila`, `3 = Poker`).
4. **EtherNet/IP Out node** writes the product ID into a PLC tag (e.g. `Product_Select`) using the Allen-Bradley Ethernet/IP node.
5. PLC receives the update and, if allowed, executes the production for the selected product.

### Files
- `NodeRED/node-red-flow-proyecto-final.json` — import to Node-RED
- `API/google_trends_api/` — Flask app code (see next section)

---

## Flask API (Google Trends wrapper)

### Purpose
Fetch relative popularity for a small set of products (beer example in the video) and return the top product ID.

### Minimal structure (example)
/google_trends_api/
├─ app.py # Flask server, endpoint: /api/top-product
├─ requirements.txt
└─ README.md

### Example endpoint behaviour
- `GET /api/top-product` → returns JSON:
```json
{
  "top_product_id": 2,
  "name": "Águila",
  "score": 78
}
```
Node-RED calls this endpoint and writes top_product_id to the PLC.

The video used a Flask app deployed to PythonAnywhere to make the service accessible to Node-RED over the internet.

### Ignition SCADA (supervision & control)
Main features implemented

* **Login/roles:** Supervisor login required to change the selected product (security).

* **Controls:** Start / Stop, manual product buttons (1, 2, 3).

* **Status & animation:** Visualization of elevator position, conveyor states, motors, LEDs and where sensors are active.

* **Counters & history:** Display of items per pallet, total packaged items and historical records per product.

* **Alarms:** Critical alarms when elevator is moving or robot is in operation to prevent unsafe interactions.

![SCADA](https://github.com/GabyCastroB/SCADA-Studio5000/blob/main/Images/Ignition.png)

### Credits / Authors

* Gabriela María Castro Beltran

* David Medina Borja

* David Andrés Ricaurte de Lima


📍 *Universidad Nacional de Colombia – Facultad de Ingeniería*  
👨‍🏫 *Profesor: Eduardo Barrera Gualdron*