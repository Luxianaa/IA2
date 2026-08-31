# Entorno e instalaciones (resumen)

Este README resume las librerías que instalaste en la terminal del workspace y cómo verificar/usar la virtualenv en Windows PowerShell.

## Entorno Python
- Virtual environment localizado en: `c:\Users\lucia\Desktop\IA 2-2025\venv\`
- Ejecutable Python (uso en la sesión):
  `C:/Users/lucia/Desktop/IA 2-2025/venv/Scripts/python.exe`
- Versión de Python usada al configurar: 3.10

Para activar el entorno en PowerShell (desde la carpeta del proyecto):

```powershell
& "c:/Users/lucia/Desktop/IA 2-2025/venv/Scripts/Activate.ps1"
```

Una vez activado, los comandos `python` y `pip` referirán al intérprete/entorno virtual del proyecto.

## Paquetes instalados (comandos detectados)
Estos son los paquetes que se instalaron en la terminal durante la sesión (orden aproximado):

- gymnasium
- matplotlib
- numpy
- torch
- imageio
- tqdm

Además se ejecutó una instalación adicional con extras para Gymnasium (control clásico):

```powershell
pip install "gymnasium[classic-control]"
```

### Propósito rápido de cada paquete
- `gymnasium` — entorno/repositorio de entornos de control / RL (fork/renovación de OpenAI Gym). Necesario para `Pendulum-v1` y otros entornos.
- `gymnasium[classic-control]` — instala dependencias extra necesarias para entornos de control clásico (p. ej. `Pendulum`, `CartPole`).
- `matplotlib` — gráficos (plots, guardado de figuras como `pendulum.png`).
- `numpy` — operaciones numéricas y arrays.
- `torch` — PyTorch (redes neuronales / deep learning) — se instaló aunque el notebook actual usa Q-learning discretizado; puede usarse para (D)RL más avanzado.
- `imageio` — lectura/escritura de imágenes y creación de GIFs/frames.
- `tqdm` — barras de progreso para bucles.

## Verificar la instalación y versiones
Con el entorno activado en PowerShell, puedes comprobar las versiones y que la instalación es correcta: 

```powershell
& "c:/Users/lucia/Desktop/IA 2-2025/venv/Scripts/python.exe" -m pip show gymnasium matplotlib numpy torch imageio tqdm
& "c:/Users/lucia/Desktop/IA 2-2025/venv/Scripts/python.exe" -c "import gymnasium as gym; print('gymnasium', gym.__version__)"
& "c:/Users/lucia/Desktop/IA 2-2025/venv/Scripts/python.exe" -c "import torch; print('torch', torch.__version__)"
& "c:/Users/lucia/Desktop/IA 2-2025/venv/Scripts/python.exe" -c "import numpy as np; print('numpy', np.__version__)"
```

Si `gymnasium[classic-control]` fue instalado con éxito, los entornos clásicos deberían funcionar:

```powershell
& "c:/Users/lucia/Desktop/IA 2-2025/venv/Scripts/python.exe" -c "import gymnasium as gym; env = gym.make('Pendulum-v1'); print('Pendulum OK', env.observation_space, env.action_space); env.close()"
```

## Reproducir la instalación (requirements)
Si quieres recrear exactamente este conjunto de paquetes en otra máquina o venv, puedes crear un `requirements.txt` e instalarlo con `pip install -r requirements.txt`.

Ejemplo mínimo para `requirements.txt` (ajusta versiones si lo deseas):

```
gymnasium
"gymnasium[classic-control]"
matplotlib
numpy
torch
imageio
tqdm
```

Instalar desde ese archivo:

```powershell
& "c:/Users/lucia/Desktop/IA 2-2025/venv/Scripts/python.exe" -m pip install -r requirements.txt
```

## Notas y recomendaciones
- Si planeas renderizar entornos (ventana gráfica) en Windows, asegúrate de tener dependencias del sistema necesarias y permisos para abrir ventanas desde el proceso Python.
- Para usar entornos que requieren dependencias extra (por ejemplo entornos Atari o de MuJoCo) instala los extras correspondientes.
- Si quieres que cree el `requirements.txt` automáticamente con las versiones actuales (`pip freeze > requirements.txt`) dímelo y lo genero.

---
Si quieres, puedo:
- Crear el archivo `requirements.txt` con las versiones actuales y añadirlo al repo.
- Añadir instrucciones para entrenar el notebook `pendulun.ipynb` automáticamente (script para lanzar X episodios y guardar `pendulum.pkl`).

¿Qué prefieres que haga a continuación?