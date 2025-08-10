# syntax=docker/dockerfile:1
FROM node:16-bullseye-slim

ENV CK_API_ENV=prod
ENV HOST=0.0.0.0
ENV PORT=3000

RUN apt-get update && apt-get install -y --no-install-recommends python3 build-essential && rm -rf /var/lib/apt/lists/*

WORKDIR /workspace
RUN mkdir -p /workspace/node_modules

COPY ./dist /workspace/dist
COPY ./package.json /workspace/package.json

RUN npm install --production --save-exact

EXPOSE 3000
CMD ["npm","start"]
