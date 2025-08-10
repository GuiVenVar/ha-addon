# syntax=docker/dockerfile:1
FROM node:16-bullseye-slim

ENV CK_API_ENV=prod
ENV HOST=0.0.0.0
ENV PORT=3000

RUN apt-get update && apt-get install -y --no-install-recommends python3 build-essential \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /workspace

# 1) instalar deps (con dev) para poder compilar
COPY ./package.json /workspace/package.json
COPY ./package-lock.json /workspace/package-lock.json
RUN npm ci

# 2) compilar TS → JS
COPY ./tsconfig.json /workspace/tsconfig.json
COPY ./src /workspace/src
RUN npm run build

# 3) dejar solo deps de producción
RUN npm prune --production

EXPOSE 3000
CMD ["node","dist/index.js"]
