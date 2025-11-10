# Quiz 2 - PyBullet Industrial Robotics

**Autores:** Sitven Sosa, Yossed Riaño Dakja

Simulación de brazos robóticos en Python usando **PyBullet**.  
Este proyecto incluye ejemplos funcionales de robots como **UR5** y KUKA, con simulación en tiempo real y movimiento de articulaciones.

---

## Instalación

1. Clona el repositorio:

```bash
git clone https://github.com/tu_usuario/PyBullet_Industrial_Robotics_Gym.git
cd PyBullet_Industrial_Robotics_Gym

```
<img width="1464" height="238" alt="image" src="https://github.com/user-attachments/assets/bfabcb6a-bfea-42f2-8bf9-f1ad889ee5ea" />


## Crear un entorno virtual y activarlo: 


```bash
python -m venv venv
# En Windows:
.\venv\Scripts\activate
# En Linux/Mac:
source venv/bin/activate
```


<img width="1397" height="485" alt="image" src="https://github.com/user-attachments/assets/29191b3f-ac69-4a2f-93d9-a8e9cb22683c" />

## Crear un entorno virtual y activarlo: 

```bash
pip install pybullet
```
<img width="902" height="386" alt="image" src="https://github.com/user-attachments/assets/2795cc7a-251e-4ac9-a11e-888bf3c87262" />

<img width="1460" height="544" alt="image" src="https://github.com/user-attachments/assets/2f774ca8-1c6e-4582-bff0-b3a092696ee8" />

## Crear un entorno virtual y activarlo: 

```bash
python -c "import pybullet; print(pybullet.getAPIVersion())"

```


## Estructura archivos:

PyBullet_Industrial_Robotics_Gym/
│
├─ venv/                   # Entorno virtual
├─ show_ur5_simple.py      # Script de ejemplo UR5
├─ show_kuka.py            # Script de ejemplo KUKA
└─ README.md


## Codifo de ejemplo Urf

```bash
import pybullet as p
import pybullet_data
import time

# Iniciar simulación con GUI
p.connect(p.GUI)
p.setGravity(0, 0, -9.81)

# Agregar el plano
p.setAdditionalSearchPath(pybullet_data.getDataPath())
plane = p.loadURDF("plane.urdf")

# Cargar UR5 desde PyBullet
ur5 = p.loadURDF("ur5/ur5.urdf", useFixedBase=True)

# Obtener cantidad de articulaciones
num_joints = p.getNumJoints(ur5)
print("Número de articulaciones:", num_joints)

# Mover articulaciones lentamente
for i in range(200):
    for j in range(num_joints):
        p.setJointMotorControl2(ur5, j, p.POSITION_CONTROL, targetPosition=(i/200)*1.5)
    p.stepSimulation()
    time.sleep(1./240.)

# Mantener ventana abierta
while True:
    time.sleep(0.1)
```

## Ejecuccion:

```bash
python show_ur5_simple.py
```

##  Robots

Agrega aquí capturas de pantalla de tu instalación, ejecución o errores resueltos:

<img width="1278" height="974" alt="image" src="https://github.com/user-attachments/assets/26de9b42-6690-41fa-9cdc-14ae5005fd74" />

<img width="1271" height="975" alt="image" src="https://github.com/user-attachments/assets/5cbff338-3d48-4b11-bca5-c6635ba98571" />

## instalacion xacro:

<img width="1275" height="448" alt="image" src="https://github.com/user-attachments/assets/d15fdd17-f772-4f09-8280-9490adedd3ae" />

##  Conclusiones

- La simulación de brazos robóticos con PyBullet permite **visualizar el comportamiento de articulaciones y movimientos** antes de implementarlo físicamente.  
- Configurar correctamente el entorno virtual y las librerías garantiza que la simulación funcione de manera estable y reproducible.  
- Manipular los parámetros como gravedad, velocidad de las articulaciones y posición inicial del robot ayuda a **entender el impacto de estas variables en la simulación**.  
- Este proyecto sirve como base para **desarrollos más complejos**, como control de robots, pick & place o integración con sensores.

---

##  Observaciones y aprendizajes

- PyBullet es **muy flexible y ligero**, lo que permite trabajar con diferentes modelos de robots sin complicaciones.  
- Los archivos URDF son fundamentales para definir la estructura física y cinemática del robot; entenderlos facilita la personalización.  
- La práctica refuerza conceptos de **cinemática, control de motores y simulación en tiempo real**.  
- Se recomienda documentar bien cada script y mantener un **README completo y visual**, incluyendo imágenes o GIFs, para que otros puedan replicar el proyecto fácilmente.  

---

##  Posibles mejoras o ampliaciones

- Agregar soporte para **más tipos de robots** (KUKA, ABB, UR10, etc.).  
- Implementar **trayectorias complejas** y control avanzado de las articulaciones.  
- Integrar **sensores virtuales** para simulaciones más realistas (cámaras, LiDAR, sensores de fuerza).  
- Crear **interfaces gráficas** para manipular la simulación de manera interactiva.  
- Generar **capturas automáticas o GIFs** de las simulaciones para documentar resultados y avances.




