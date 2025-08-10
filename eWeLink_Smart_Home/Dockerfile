# syntax=docker/dockerfile:1
FROM node:16-bullseye-slim

ENV CK_API_ENV=prod
ENV HOST=0.0.0.0
ENV PORT=3000

RUN apt-get update && apt-get install -y --no-install-recommends python3 build-essential \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /workspace

# Instala solo deps de producción a partir de package.json
COPY ./package.json /workspace/package.json
RUN npm install --production --no-audit --no-fund

# Copia el build ya generado
COPY ./dist /workspace/dist

EXPOSE 3000
CMD ["node","start"]
