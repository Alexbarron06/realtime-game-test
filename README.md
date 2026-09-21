# Juego Realtime con ID + sesión temporal + bloqueo por dispositivo

## Incluye
- `index.html`: juego en PC/TV.
- `control.html`: control móvil.
- `config.js`: conexión Supabase.
- `setup.sql`: crea el historial y la función de acceso.

## Comportamiento
1. El usuario abre el control móvil.
2. Ingresa su ID.
3. El ID se registra, pero no se valida.
4. El navegador genera un `device_id` con `crypto.randomUUID()` y lo guarda en `localStorage`.
5. Supabase consulta el histórico de ese `device_id`.
6. Si está disponible, habilita el control por 60 segundos.
7. Al terminar, el dispositivo queda bloqueado 3 minutos adicionales.
8. Después puede iniciar otra sesión.

## Instalar
### 1) Supabase
Ve a `SQL Editor > New query`, pega todo `setup.sql` y ejecútalo.

### 2) GitHub Pages
Reemplaza los archivos actuales del repositorio por:
- `index.html`
- `control.html`
- `config.js`

Puedes conservar `setup.sql` y `README.md` también en el repositorio si quieres.

### 3) Probar
PC:
`https://alexbarron06.github.io/realtime-game-test/?room=prueba1`

Celular:
`https://alexbarron06.github.io/realtime-game-test/control.html?room=prueba1`

## Historial
En Supabase podrás ver la tabla `game_sessions` con:
- student_id
- device_id
- room
- started_at
- control_ends_at
- cooldown_ends_at

## Nota
Este bloqueo no usa IMEI, MAC ni fingerprinting. Si alguien borra el almacenamiento del navegador, usa incógnito u otro navegador, puede recibir un nuevo `device_id`.
