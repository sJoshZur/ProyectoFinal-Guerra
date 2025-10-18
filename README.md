# 🇧🇴 Juego de Preguntas: Independencia de Bolivia GUERRA

## 📖 Descripción del Sistema

Este proyecto es un juego educativo interactivo desarrollado en **GameMaker Studio 2** que permite a los usuarios aprender sobre la Independencia de Bolivia de manera divertida y competitiva. El juego combina un sistema de preguntas y respuestas con un registro de progreso personal.

---

## 🎮 ¿Cómo funciona?

El juego está dividido en tres pantallas principales que se conectan entre sí:

### 1️⃣ Pantalla de Inicio
- El jugador ingresa su nombre de usuario
- Se muestra el título y tema del juego
- Botón para comenzar la partida

### 2️⃣ Pantalla de Juego
- El jugador responde preguntas sobre la Independencia de Bolivia
- Dispone de **120 segundos** para responder el máximo de preguntas
- Cada pregunta tiene 4 opciones de respuesta
- El puntaje aumenta con cada respuesta correcta
- Se muestra el temporizador en tiempo real

### 3️⃣ Pantalla de Resultados
- Muestra el puntaje obtenido en la partida
- Cantidad de respuestas correctas
- Mejor puntaje registrado del jugador
- Total de partidas jugadas
- Opción para reintentar

---

## 💾 Sistema de Guardado

El juego utiliza un **sistema de almacenamiento local** que guarda automáticamente:

- **Nombre del jugador:** Se registra al ingresar por primera vez
- **Mejor puntaje:** Se actualiza si superas tu récord anterior
- **Total de partidas:** Cuenta cuántas veces has jugado
- **Respuestas correctas acumuladas:** Total de preguntas respondidas correctamente en todas las partidas
- **Archivo de almacenamiento:** Se guarda en `jugadores.ini` en la carpeta del juego

Cada vez que terminas una partida, tus datos se guardan automáticamente, permitiéndote seguir tu progreso.

---

## 🧠 Las Preguntas

El juego incluye **10 preguntas fijas** cuidadosamente seleccionadas sobre:

- Año de la Independencia de Bolivia (1825)
- Figuras clave: Antonio José de Sucre, Simón Bolívar
- Ubicación de la proclamación (Sucre/Chuquisaca)
- Nombre anterior del país (Alto Perú)
- Batallas importantes
- Documentos históricos (Acta de Independencia)
- Duración de la guerra de independencia

Las preguntas se repiten en orden para que sigas aprendiendo con cada partida.

---

## 🎯 Sistema de Puntaje

- **Cada respuesta correcta:** +10 puntos
- **Cada respuesta incorrecta:** 0 puntos
- **Tiempo límite:** 120 segundos por partida
- **Puntaje máximo posible:** 100 puntos (si respondes correctamente las 10 preguntas)

---

## 📊 Estadísticas del Jugador

El juego registra y muestra:

| Estadística | Descripción |
|------------|------------|
| **Mejor puntaje** | El puntaje más alto alcanzado |
| **Total de partidas** | Cuántas veces has jugado |
| **Preguntas correctas** | Total acumulado de respuestas correctas |
| **Progreso actual** | Se ve en tiempo real durante la partida |

---

## ⏱️ Dinámica del Tiempo

- **Duración total:** 120 segundos (2 minutos)
- **Tiempo por pregunta:** Variable según tu velocidad
- **Temporizador visible:** Se muestra en rojo en la pantalla de juego
- **Automático:** Cuando llega a 0, la partida termina

---

## 🕹️ Cómo Jugar

1. **Ingresa tu nombre** en la pantalla de inicio
2. **Haz clic en "COMENZAR"** para iniciar el juego
3. **Lee la pregunta** que aparece en pantalla
4. **Presiona el número** (1, 2, 3 o 4) correspondiente a tu respuesta
5. **Continúa respondiendo** hasta que se acabe el tiempo
6. **Ve tus resultados** en la pantalla final
7. **Reinicia el juego** si quieres jugar de nuevo

---

## 🔄 Flujo del Juego

```
Inicio
   ↓
Ingresar nombre
   ↓
Comenzar partida (120 segundos)
   ↓
Responder preguntas
   ↓
¿Se acabó el tiempo?
   ↓ Sí
Ver resultados y guardar datos
   ↓
¿Reintentar?
   ↓ Sí → Volver a inicio
   ↓ No → Cerrar juego
```

---

## 📱 Características Técnicas

- **Guardado automático:** Cada partida se guarda sin intervención del usuario
- **Información persistente:** Los datos se mantienen entre sesiones
- **Interfaz simple:** Diseño limpio y enfocado en el aprendizaje
- **Retroalimentación en tiempo real:** Ves tu puntaje y el tiempo mientras juegas
- **Gestión de datos:** Sistema organizado que evita pérdida de información

---

## 🎓 Objetivo Educativo

El juego busca:

- **Reforzar conocimientos** sobre la historia de Bolivia
- **Generar competencia sana** mediante puntajes y mejores récords
- **Hacer el aprendizaje divertido** con dinámicas de tiempo y puntuación
- **Permitir seguimiento de progreso** para motivar al jugador

---

## 🚀 Próximas Mejoras Planeadas

- Agregar más preguntas sobre diferentes épocas de Bolivia
- Sistema de niveles de dificultad
- Clasificación de jugadores (ranking)
- Efectos de sonido y música de fondo
- Temas visuales personalizables
- Versión móvil del juego

---

## 📋 Resumen Técnico

| Componente | Detalles |
|-----------|----------|
| **Motor** | GameMaker Studio 2 |
| **Lenguaje** | GML (GameMaker Language) |
| **Almacenamiento** | Archivo INI local |
| **Duración de partida** | 120 segundos |
| **Cantidad de preguntas** | 10 |
| **Opciones por pregunta** | 4 (opción múltiple) |
| **Puntaje por acierto** | 10 puntos |
| **Plataformas compatibles** | Windows, Mac, Linux |

---
