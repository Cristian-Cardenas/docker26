# Cristian Camilo Cardenas Carvajal

Se montó una app de 3 piezas (API FastAPI, PostgreSQL, Nginx-proxy) en contenedores Docker con Dockerfile multi-etapa, orquestadas con docker-compose.yml en red interna más volumen persistente. Se crearon 2 actions que se ejecutan en cada PR/push a main:

publicar-imagen.yml — Al hacer push a main o crear un tag v*.*.*, construye la imagen Docker y la publica en GHCR con etiquetas latest, SHA y versión.

verificacion.yml — En cada PR/push a main, valida el docker-compose.yml, construye la imagen, levanta los servicios y comprueba que /health y /db respondan.