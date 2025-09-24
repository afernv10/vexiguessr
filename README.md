


# 🌍 Quiz de Mapas Multijugador

Un juego estilo GeoGuessr / Kahoot en el que los jugadores deben marcar en el mapa el lugar correcto en base a preguntas.  
Se juega en vivo de forma sincronizada con un **host** que controla las rondas, y varios jugadores que se conectan desde sus dispositivos.  

---

## 🚀 Características
- Mapa interactivo con [Leaflet](https://leafletjs.com/).
- Preguntas configurables desde un JSON externo (`preguntas.json`).
- Puntuación calculada por:
  - Distancia al punto real.
  - Tiempo restante en el contador.
- Ranking en vivo:
  - **Intermedio** entre rondas.
  - **Final** al terminar la partida.
- Modo **host** para controlar el ritmo del juego.
- Almacenamiento y sincronización con **Firebase Realtime Database**.

---

## 🛠️ Requisitos
- Servidor estático (ej: `Live Server` en VSCode o `http-server` de npm).
- Una cuenta de Firebase configurada en modo Realtime Database.
- Fichero `firebaseConfig.js` con tu configuración.

Ejemplo de `firebaseConfig.js`:
```js
// firebaseConfig.js
export default {
  apiKey: "XXXX",
  authDomain: "XXXX.firebaseapp.com",
  databaseURL: "https://XXXX.firebaseio.com",
  projectId: "XXXX",
  storageBucket: "XXXX.appspot.com",
  messagingSenderId: "XXXX",
  appId: "XXXX"
};


---

## ▶️ Uso

### 1. Arrancar servidor local

```bash
npx http-server
```

o

```bash
live-server
```

### 2. Modo jugador

Abrir en el navegador:

```
http://localhost:8080/index.html
```

* Introducir nombre.
* Esperar a que el host inicie partida.

### 3. Modo host

Abrir en el navegador:

```
http://localhost:8080/index.html?host=1
```

* Controles disponibles:

  * **Iniciar partida**
  * **Siguiente pregunta**
  * **Finalizar partida**

---

## 📝 Personalización de preguntas

En el archivo `preguntas.json` puedes definir tus preguntas:

```json
[
  {
    "text": "¿Dónde está la Torre Eiffel?",
    "lat": 48.8584,
    "lng": 2.2945
  },
  {
    "text": "¿Dónde se encuentra la Sagrada Familia?",
    "lat": 41.4036,
    "lng": 2.1744
  }
]
```

---

## ⚡ Flujo del juego

1. El host inicia la partida → la primera pregunta aparece en todos los dispositivos.
2. Los jugadores seleccionan un punto en el mapa y confirman.
3. Se calcula puntuación automáticamente.
4. Al acabar la ronda, se muestra **ranking intermedio**.
5. El host pasa a la siguiente pregunta.
6. Al terminar todas las preguntas, se muestra el **ranking final**.

---

## 📌 Notas

* Para empezar una **nueva partida limpia**, el host borra resultados previos de Firebase al pulsar *Iniciar partida*.
* El botón **Comprobar respuesta** se deshabilita una vez respondida la pregunta.
* Las respuestas duplicadas están bloqueadas: cada jugador solo puede enviar una por ronda.

---

## 👥 Créditos

Proyecto educativo basado en:

* [Leaflet](https://leafletjs.com/)
* [Firebase Realtime Database](https://firebase.google.com/)
* Inspirado en GeoGuessr y Kahoot.
