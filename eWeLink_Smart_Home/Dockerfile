# ARG BUILD_FROM
# FROM $BUILD_FROM

FROM node:14-slim
FROM node:18-bullseye-slim
ENV CK_API_ENV=prod
RUN apt-get update \ && apt-get install -y --no-install-recommends python3 build-essential \ && rm -rf /var/lib/apt/lists/*
RUN mkdir -p /workspace/node_modules
COPY ["./dist", "./package.json", "/workspace/"]
WORKDIR /workspace
RUN npm install --production --save-exact
COPY ["./node_modules", "/workspace/node_modules/"]
EXPOSE 3000
CMD npm start
