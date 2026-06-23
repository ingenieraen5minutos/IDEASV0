# IDEAS v0 - Adquisición de datos

Repositorio de apoyo para la **Práctica 1: Adquisición de datos con el kit IDEAS v0**.
El proyecto permite adquirir, visualizar y guardar datos experimentales de un motor DC N20 con encoder, usando Arduino, un sensor de corriente INA240 y una interfaz gráfica desarrollada en Python.

La práctica introduce conceptos básicos de sensores, comunicación serial, adquisición de datos, visualización en tiempo real y análisis experimental de sistemas físicos.

---

## Archivos incluidos

| Archivo               | Descripción                                                                                                                                                                          |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `ArduinoGetData.ino`  | Programa para Arduino UNO/Nano. Lee los pulsos del encoder y la corriente medida con el sensor INA240. Envía los datos por comunicación serial a 115200 baudios.                     |
| `practicaGetData.py`  | Interfaz gráfica en Python para seleccionar el puerto COM, elegir la práctica, iniciar la adquisición, visualizar las señales en tiempo real y guardar los datos en archivos `.csv`. |
| `practicaGetData.pdf` | Manual de usuario de la práctica. Explica el objetivo, materiales, conexiones, carga del programa en Arduino, uso de la interfaz en Python y generación de datos.                    |

---

## Objetivo de la práctica

Adquirir datos experimentales del funcionamiento de un motor DC mediante el kit IDEAS v0. En particular, se registran:

* **Tiempo** en milisegundos (`t_ms`).
* **Velocidad** del motor en RPM (`rpm`), calculada a partir de los pulsos del encoder.
* **Corriente eléctrica** consumida por el motor en miliamperes (`current_mA`).

Los datos se muestran en tiempo real mediante gráficas y se guardan en archivos `.csv` para análisis posteriores.

---

## Requisitos de software

### Arduino

* Arduino IDE.
* Tarjeta Arduino UNO o compatible.

### Python

Se recomienda usar Python 3.10 o superior.

Instalar las dependencias con:

```bash
pip install numpy customtkinter pyserial matplotlib scipy
```

> `scipy` se utiliza para el filtro Butterworth en la práctica 3. Si no se instala, el resto de la aplicación puede funcionar, pero ese filtro quedará deshabilitado.

---

## Cómo usar el proyecto

### 1. Cargar el programa en Arduino

1. Abrir `ArduinoGetData.ino` en Arduino IDE.
2. Seleccionar la tarjeta Arduino correspondiente.
3. Seleccionar el puerto COM detectado.
4. Cargar el programa en la tarjeta.
5. Abrir el monitor serial a `115200 baudios` para verificar que el Arduino envía datos correctamente.
6. Cerrar el monitor serial antes de ejecutar Python, para evitar conflictos con el puerto COM.

### 2. Ejecutar la interfaz en Python

Desde la carpeta del proyecto, ejecutar:

```bash
python practicaGetData.py
```

Después:

1. Seleccionar el puerto COM del Arduino.
2. Elegir la práctica deseada.
3. Configurar la duración post-trigger.
4. Presionar **Iniciar adquisición**.
5. Encender el motor usando el botón del kit.
6. Observar las gráficas en tiempo real.
7. Revisar los archivos generados al finalizar.

---

## Archivos generados

Los datos adquiridos se guardan automáticamente en la carpeta:

```text
datos/
```

Los archivos principales se guardan en formato `.csv`, por ejemplo:

```text
ideas_v0_P1_20260620_165942.csv
ideas_v0_P1_20260620_165942_meta.txt
```

El archivo `.csv` contiene las muestras experimentales. El archivo `_meta.txt` contiene información adicional del ensayo, como fecha, práctica, modo de adquisición, puerto COM y parámetros utilizados.

---

## Créditos

Proyecto desarrollado como material de apoyo para **Ingeniería en 5 minutos**, enfocado en el aprendizaje práctico de adquisición de datos, sensores, programación e identificación de sistemas.
