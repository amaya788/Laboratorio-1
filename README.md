# 🔬 Laboratorio 1 - Comunicaciones Industriales

**Universidad Santo Tomás**  
**Autores:** David Esteban Díaz Castro, Ferney Arturo Amaya Gómez, Jhonny Alejandro Mejía  
**Fecha:** Septiembre 1, 2025  

---

## 📑 Contenido
1. [Repasando conceptos](#-1-repasando-conceptos)  
   - Componentes de un Microcontrolador  
   - Interrupciones y reloj de 16 MHz  
   - Raspberry Pi vs Arduino  
   - Sistema operativo y GPIO en Raspberry Pi  
   - Convertidor analógico-digital  
2. [UART Asíncrono con Paridad y Visualización LED](#-2-uart-asíncrono-con-paridad-y-visualización-led)  
3. [SPI Sincrónico con Control LED](#-3-spi-sincrónico-con-control-led)  
4. [I2C con Sensor y LEDs](#-4-i2c-con-sensor-y-leds)  
5. [Referencias](#-5-referencias)  

---

## 📘 1. Repasando conceptos

### 🔹 1.1 Componentes de un Microcontrolador
Un microcontrolador como el **ATmega328P** del Arduino Uno es una pequeña computadora con:  
- Procesador  
- Memoria de programa y datos  
- Pines de entrada/salida (I/O)  

Permite ejecutar instrucciones, leer sensores y controlar actuadores mediante comunicación serial (TX/RX).

### 🔹 1.2 Interrupciones y Reloj de 16 MHz
- **Interrupciones:** alertas que interrumpen el flujo del programa para atender eventos urgentes.  
- **Reloj de 16 MHz:** sincroniza operaciones → ~2 a 4 millones de instrucciones por segundo.  

### 🔹 1.3 Raspberry Pi vs Arduino
- **Raspberry Pi:** computadora en miniatura, corre un SO, multitarea, conectividad avanzada.  
- **Arduino:** microcontrolador, no requiere SO, ideal para control en tiempo real.  

### 🔹 1.4 Sistema Operativo y GPIO en Raspberry Pi
- Necesita Linux u otro OS para multitarea.  
- GPIO configurables como entradas o salidas programables.  

### 🔹 1.5 Convertidor Analógico-Digital
- Arduino trae **ADC integrado** para leer señales analógicas.  
- Raspberry Pi necesita **ADC externo** (solo procesa señales digitales).  

---

## 💡 2. UART Asíncrono con Paridad y Visualización LED

**Objetivo:** Transmitir datos con detección de errores (paridad) y visualizar éxito/error con LEDs.  

**Materiales:**  
- Arduino Uno  
- Raspberry Pi 3  
- 2 LEDs + resistencias de 1kΩ  
- Jumpers  

**Ruta de conexiones:**  
- Comunicación vía **USB (Serial integrado)** → Raspberry detecta al Arduino como puerto serie.  

**Desarrollo:**  
1. Instalación de Arduino IDE en Raspberry (`sudo apt-get install arduino`).  
2. Carga del código en Arduino.  
3. Comunicación con Raspberry Pi vía Thonny.  

**Resultados:**  
- Comunicación bidireccional entre Arduino ↔ Raspberry.  
- Visualización en **LEDs** según la paridad de los datos transmitidos.  

---

## 🔄 3. SPI Sincrónico con Control LED

**Objetivo:** Transferir datos vía **SPI**, controlando LEDs en Arduino (esclavo).  

**Desarrollo:**  
- Conexión directa **MOSI, MISO, SCK y SS** entre Raspberry (maestro) y Arduino (esclavo).  
- Código en Thonny para enviar comandos SPI.  

**Resultados:**  
- LED en Arduino enciende y apaga cada 2 segundos.  
- Raspberry muestra la respuesta SPI en consola.  

---

## 📡 4. I2C con Sensor y LEDs

**Objetivo:** Leer un **potenciómetro en Arduino** y mostrar el valor en Raspberry usando LEDs.  

**Desarrollo:**  
1. Código en Arduino para lectura de entrada analógica.  
2. Raspberry recibe valores y los representa en 3 LEDs según los 3 bits más significativos.  

**Resultados:**  
- Rango de lectura: **0 a 255**.  
- LEDs en Raspberry varían de acuerdo al valor leído en el potenciómetro.  

---

## 📚 5. Referencias
1. Interrupciones con Arduino a través de un ejemplo práctico. *Programarfacil Arduino y Home Assistant*, 2016.  
   👉 [programarfacil.com](https://programarfacil.com/blog/arduino-blog/interrupciones-con-arduino-ejemplo-practico/)  

---

> 📌 **Nota:** Este laboratorio permitió comparar las comunicaciones **UART, SPI e I2C** entre **Arduino y Raspberry Pi**, reforzando conceptos de detección de errores y control con periféricos.
