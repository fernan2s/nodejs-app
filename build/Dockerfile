ARG ARCH=
#ARG IMAGE_BASE=16.3.0-alpine
ARG IMAGE_BASE=18.3.0-alpine

FROM ${ARCH}node:$IMAGE_BASE
LABEL Name="Node.js Demo App" Version=4.8.5
LABEL org.opencontainers.image.source = "https://github.com/benc-uk/nodejs-demoapp"
ENV NODE_ENV production
ARG WEATHER_API_KEY=bfd214beff0c9bcb3c79470fd7a36406
WORKDIR /app 

# For Docker layer caching do this BEFORE copying in rest of app
COPY src/package*.json ./
RUN npm install prom-client --force
RUN npm install --production --silent
RUN apk upgrade

# NPM is done, now copy in the rest of the project to the workdir
COPY src/. .

# Port 3000 for our Express server 
EXPOSE 3000
ENTRYPOINT ["npm", "start"]
