# BUG HUNTERS

Juego competitivo para ISND con dos jugadores, celulares como interfaz de respuesta y pantalla pública.

## Incluye

- 2 jugadores por sala.
- Registro por ID.
- 8 rondas de 12 segundos.
- Errores de sintaxis, lógica y seguridad.
- Dificultad progresiva.
- Bonus por rapidez.
- Puntaje calculado por Supabase.
- Marcador público.
- Ranking global persistente por ID.
- QR generado en la pantalla.
- Salas independientes mediante `?room=`.

## Archivos

- `index.html` — pantalla pública / host.
- `player.html` — interfaz del celular.
- `config.js` — Supabase.
- `setup.sql` — tablas, preguntas y funciones RPC.
- `README.md`.

## Paso 1 — Supabase

En tu proyecto actual:

1. Abre `SQL Editor`.
2. `New query`.
3. Pega TODO el contenido de `setup.sql`.
4. Pulsa `Run`.

Las tablas tienen prefijo `bug_`, así que no interfieren con la prueba anterior.

El juego utiliza Realtime Broadcast para sincronización y RPC para puntajes/respuestas. Supabase mantiene las respuestas correctas y calcula el tiempo del servidor.

## Paso 2 — GitHub

Recomendado: crear repositorio `bug-hunters`.

Sube a la raíz:

- `index.html`
- `player.html`
- `config.js`

Activa GitHub Pages:

`Settings -> Pages -> Deploy from a branch -> main -> /root`

Con tu usuario, la dirección esperada será:

Pantalla:
`https://alexbarron06.github.io/bug-hunters/?room=BUG01`

Celulares:
`https://alexbarron06.github.io/bug-hunters/player.html?room=BUG01`

La pantalla genera automáticamente el QR correcto para su sala.

## Flujo

1. Abres `index.html` en la PC/TV.
2. Jugador 1 escanea QR e ingresa ID.
3. Jugador 2 escanea QR e ingresa ID.
4. Al haber 2 jugadores, inicia automáticamente.
5. Cada ronda muestra el mismo código a ambos.
6. Cada jugador responde A/B/C/D desde su celular.
7. Supabase calcula puntos y tiempo.
8. Si ambos responden, la ronda puede cerrar antes.
9. Al final aparece ganador + Top 10 global.

## Formato de rondas

1. Sintaxis — nivel 1
2. Lógica — nivel 1
3. Sintaxis — nivel 2
4. Lógica — nivel 2
5. Seguridad — nivel 1
6. Seguridad — nivel 2
7. Lógica — nivel 3
8. Seguridad — nivel 3

## Desempate

1. Mayor puntuación.
2. Mayor número de aciertos.
3. Menor tiempo total de respuesta.

## Torneos

Puedes abrir varias salas simultáneas:

`?room=GRUPO1`
`?room=GRUPO2`
`?room=SEMIFINAL-A`
`?room=FINAL`

Cada pantalla y sus dos celulares deben usar el mismo `room`.
