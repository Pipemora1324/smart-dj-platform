# Smart DJ Platform

Plataforma local para gestión musical de venues: frontend público, gateway Nginx, API Express, PostgreSQL, Redis/BullMQ y motor FastAPI/librosa.

## Ejecutar

1. Copia `.env.example` como `.env` y reemplaza las claves JWT y contraseña de base de datos (para la demostración ya se incluye un `.env` local).
2. Ejecuta `docker compose up --build`.
3. Abre `http://localhost:8080`.

El único origen expuesto es el gateway en el puerto 8080. Crea una cuenta, registra el establecimiento y comparte el código que se muestra con clientes para enviar solicitudes a `POST /api/public/venues/:code/requests`.

## Servicios

| Servicio | Responsabilidad |
| --- | --- |
| gateway | Punto de entrada, reverse proxy y límite de 5 intentos de login/minuto por IP |
| frontend | Landing y alta de establecimientos |
| backend | REST, tokens JWT y cookies HttpOnly, cola y persistencia |
| ai | BPM/tonalidad con librosa y compatibilidad/transición por heurísticas |
| postgres / redis | Datos relacionales, caché, pub/sub y BullMQ |
