🌿 Yachay Runa - Gamified Language Learning Prototype

¡Bienvenido a Yachay Runa! Una aplicación web interactiva y gamificada diseñada para enseñar lenguas originarias del Perú (Quechua, Asháninka) y expresiones culturales de la Costa, utilizando mecánicas de retención similares a Duolingo.

🎯 Sobre el Proyecto (Disclaimer de Prototipo)

⚠️ Aviso Importante: Este proyecto es un Prototipo de Alta Fidelidad (Frontend-Only).
Ha sido construido íntegramente con HTML5, Tailwind CSS y Vanilla JavaScript en un solo archivo (index.html) para facilitar su despliegue y testeo rápido.

NO utiliza backend ni bases de datos (SQL/NoSQL). Toda la persistencia de datos (progreso del jugador, estrellas, inventario) se simula de manera local utilizando el localStorage del navegador. Si cambias de navegador o borras la caché, el progreso se reiniciará.

✨ Características Principales

Progresión por Zonas: Tres rutas culturales distintas (Costa, Sierra, Selva) con niveles secuenciales.

Economía y Tienda: Sistema de recompensas basado en Estrellas (⭐) que permite comprar artefactos históricos con descripciones interactivas (Tooltips).

Spaced Repetition System (SRS): Si el usuario falla una pregunta, el motor la envía al final de la cola, obligándolo a acertar para poder terminar el nivel.

Pop Quiz Dinámico: Un minijuego épico que extrae 10 preguntas aleatorias de un banco de 50, modificando la interfaz (UI) según el tipo de pregunta (Boss Fight, Speedrun con temporizador, Modo Debugger, etc.).

Responsive Design: Adaptado 100% para dispositivos móviles y escritorio usando Tailwind CSS.

🧠 Guía del Código Fuente (Para Desarrolladores)

Si estás explorando el código fuente (index.html), notarás que está dividido en tres pilares lógicos dentro del bloque <script>. Esta arquitectura simula un entorno MVC (Modelo-Vista-Controlador) en Vanilla JS:

1. QuestionDB y ArtifactsShop (El Modelo / Datos)

Son objetos JSON estáticos que actúan como nuestra base de datos. Contienen todo el contenido cultural, las opciones, las respuestas correctas y los precios de la tienda.

2. GameState (El Gestor de Estado)

Es el "falso backend". Este objeto centraliza las variables del jugador (nombre, estrellas, progreso) y contiene el método save() que inyecta el estado actual en el localStorage convertido en cadenas de texto JSON.

3. App (El Controlador / Interfaz)

Es el motor principal del juego. Funciones clave a observar:

startLevel(): Utiliza el Algoritmo Fisher-Yates (App.shuffle) para mezclar el banco de preguntas y selecciona una muestra (ej. 8 preguntas) para crear la misión actual.

showNextQuestion(): Inyecta el HTML dinámicamente. Escanea las etiquetas (ej. [Boss Fight]) en el texto de la pregunta para aplicar clases CSS condicionales y cambiar por completo el aspecto visual del minijuego.

checkAnswer(): Maneja la lógica de victoria/derrota. Activa las animaciones CSS (Shake/Pop-in) e implementa la lógica de repetición enviando las preguntas falladas mediante un this.missionQueue.push(q).

🚀 Instalación y Uso Local

Al ser una aplicación de una sola página (SPA) sin dependencias de Node.js, no necesitas instalar nada.

Clona este repositorio o descarga el archivo index.html.

Abre el archivo index.html en cualquier navegador web moderno (Chrome, Edge, Safari, Firefox).

¡Disfruta aprendiendo!

Proyecto creado como maqueta interactiva y prueba de concepto para la preservación lingüística.
