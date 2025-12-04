# 🎯 Detector de Gatos, Perros y Humanos

Proyecto de detección en tiempo real usando tu modelo entrenado de IA.

## 📱 Cómo usar en COMPUTADORA

1. **Abre una terminal** en la carpeta del proyecto

2. **Inicia el servidor**:
   ```bash
   python -m http.server 8000
   ```
   (Si tienes Python 2, usa: `python -m SimpleHTTPServer 8000`)

3. **Abre tu navegador** y ve a:
   ```
   http://localhost:8000/detector.html
   ```

4. **Permite el acceso a la cámara** cuando te lo pida

5. ¡Listo! Apunta la cámara a:
   - Tu cara → Detectará "Humanos"
   - Un gato → Detectará "Gatos"
   - Un perro → Detectará "Perros"

---

## 📱 Cómo usar en CELULAR

### Opción 1: Red Local (más simple)

1. **En tu computadora**, inicia el servidor (paso 2 de arriba)

2. **Encuentra tu IP local**:
   - Windows: Abre CMD y escribe `ipconfig`, busca "IPv4"
   - Mac/Linux: Abre Terminal y escribe `ifconfig` o `ip addr`, busca tu IP
   - Ejemplo: `192.168.1.100`

3. **En tu celular** (debe estar en la misma WiFi):
   - Abre el navegador
   - Ve a: `http://TU_IP:8000/detector.html`
   - Ejemplo: `http://192.168.1.100:8000/detector.html`

⚠️ **PROBLEMA**: Muchos navegadores no permiten usar la cámara con HTTP (necesitan HTTPS)

---

### Opción 2: NGROK (recomendado para celular) ✅

Esta opción crea un túnel HTTPS para que funcione la cámara en el celular.

1. **Descarga ngrok**:
   - Ve a: https://ngrok.com/download
   - Descarga e instala ngrok

2. **Inicia el servidor Python** (si no está corriendo):
   ```bash
   python -m http.server 8000
   ```

3. **Abre OTRA terminal** y ejecuta ngrok:
   ```bash
   ngrok http 8000
   ```

4. **Copia la URL HTTPS** que aparece:
   ```
   Forwarding   https://abc123.ngrok.io -> http://localhost:8000
                ^^^^^^^^^^^^^^^^^^^^^^^^
                    Copia esta URL
   ```

5. **En tu celular**:
   - Abre el navegador
   - Ve a: `https://abc123.ngrok.io/detector.html`
   - Permite el acceso a la cámara
   - ¡Funciona! 🎉

⚠️ **IMPORTANTE**:
- La URL de ngrok cambia cada vez que lo reinicias
- El túnel gratis expira después de 2 horas (solo reinicia ngrok)
- Puedes usar el celular en cualquier red (no necesita estar en la misma WiFi)

---

## 🎨 Características del detector

✅ Diseño moderno y responsive (se adapta al celular)
✅ Muestra emojis según la detección (🐱 🐶 👤)
✅ Porcentaje de confianza en tiempo real
✅ Botón para cambiar entre cámara frontal y trasera
✅ Optimizado para el modelo entrenado en Google Colab

---

## 🔧 Solución de problemas

**"No se pudo acceder a la cámara"**
- Asegúrate de dar permisos de cámara en el navegador
- En celular, usa HTTPS (opción ngrok)

**"Error al cargar el modelo"**
- Verifica que la carpeta `modelo_IA/tfjs_model/` existe
- Verifica que el archivo `modelo_IA/clases.json` existe

**La detección es lenta**
- Es normal, el modelo MobileNetV2 es pesado
- En celular puede tardar más

---

## 📁 Archivos del proyecto

```
ia-prueba/
├── detector.html          ← El detector nuevo (USA ESTE)
├── index.html            ← El detector antiguo
├── modelo_IA/
│   ├── tfjs_model/       ← Modelo convertido para web
│   │   ├── model.json
│   │   └── group1-shard*.bin
│   └── clases.json       ← Las 3 clases
└── INSTRUCCIONES.md      ← Este archivo
```

---

¡Disfruta tu detector de IA! 🚀
