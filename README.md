# Proyecto: Vocoder GAN para Conversión de Espectrogramas a Audio

Este proyecto constituye la segunda etapa de un sistema de texto a voz (TTS), donde se implementa un vocoder personalizado basado en una red Generativa Adversarial (GAN). Su propósito es convertir espectrogramas mel generados por Tacotron 2 en señales de audio naturales.

---

## 🔧 Estructura del Sistema TTS

El sistema se compone de dos etapas:

1. **Tacotron 2 (no incluido en este repositorio)**  
   Convierte texto en espectrogramas mel.

2. **GAN Vocoder (este proyecto)**  
   Transforma los espectrogramas mel en audio crudo.

---

## 📁 Archivos Importantes

- `TestTTS.ipynb`: Notebook principal con todo el flujo de trabajo.
- `README.md`: Este archivo de documentación.
- `requirements.txt`: Lista de dependencias necesarias (opcional, puede ser generado).

---

## 🧪 Dataset Utilizado

**Spoken Digit Dataset (TensorFlow Datasets)**  
- Audio de dígitos del 0 al 9 hablados por diferentes personas.
- 8 kHz de muestreo.
- Cada muestra de audio se transforma en un espectrograma mel como entrada para la GAN.

---

## 🔄 Flujo de Trabajo

### 1. Adquisición y Preprocesamiento de Datos

- Descarga del dataset desde TensorFlow Datasets.
- Cálculo de los espectrogramas mel usando `librosa`.
- Emparejamiento (mel, audio) para entrenamiento.
- Normalización de datos para estabilidad en el entrenamiento.

### 2. Diseño del Modelo GAN

#### Generador
- Arquitectura basada en LSTM.
- Entrada: secuencia de espectrogramas mel.
- Salida: señal de audio en el dominio temporal.

#### Discriminador
- LSTM bidireccional.
- Entrada: señal real o generada.
- Salida: probabilidad de autenticidad.

### 3. Funciones de Pérdida

- **Pérdida Adversarial (Binary Crossentropy)**
- **Pérdida de Reconstrucción (MSE o L1 loss)**

### 4. Entrenamiento

- Entrenamiento alternado de generador y discriminador.
- Optimización con Adam.
- Visualización periódica de señales generadas.
- Almacenamiento de métricas.

### 5. Evaluación

- Comparación de audio real vs. generado.
- Métricas implementadas:
  - MSE (Error Cuadrático Medio)
  - PSNR (Relación Señal a Ruido de Pico)
  - SNR (Relación Señal a Ruido)
- Visualización de gráficas de forma de onda y espectrogramas.

---

## ▶️ Instrucciones de Uso

### 1. Clona el repositorio

```bash
git clone https://github.com/tu_usuario/gan-vocoder-tts.git
cd gan-vocoder-tts
```

### 2. Instala las dependencias

```bash
pip install -r requirements.txt
```

### 3. Ejecuta el notebook

```bash
jupyter notebook TestTTS.ipynb
```

---

## 📊 Resultados y Visualización

- Se presentan comparativas entre señal generada y real.
- Gráficos de error y evolución del entrenamiento.
- Audio de salida que puede ser reproducido desde el notebook.

---

## 📚 Tecnologías Usadas

- Python 3.8+
- TensorFlow 2.x
- NumPy, librosa, matplotlib
- Jupyter Notebook

---

## 👨‍💻 Autor

**@homero-sepulveda**  
Ingeniero mecatrónico | Especializado en IA, sistemas embebidos y robótica.

---

## 📄 Licencia

Este proyecto es de uso académico y experimental.

---

## 📝 Notas Adicionales

- El proyecto se puede escalar para otros datasets de mayor calidad.
- Para una voz completa, debe integrarse con Tacotron 2 o un sistema similar de texto a espectrograma.
- Puede extenderse a vocoders más complejos como HiFi-GAN o WaveGAN.

