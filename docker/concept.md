# The core idea

Docker packages your app and everything it needs (runtime, libraries, config) into a container — an isolated, reproducible unit that runs identically on any machine.

## Key concepts
Dockerfile → Image → Container is the main pipeline. 
You write a Dockerfile (instructions), Docker builds it into an immutable image, and run creates a live container from it.

Image layers are the efficiency trick. Each instruction in your Dockerfile creates a layer. Layers are cached — if your package.json hasn't changed, Docker skips reinstalling dependencies. This is why you should copy dependency files before your app code.

`docker-compose` is for multi-container apps. Instead of manually starting a web server, database, and cache separately, one docker-compose up starts them all together on a shared private network, where they reach each other by service name (e.g. db:5432).

Volumes solve the ephemeral problem. Containers are stateless by default — kill one and its data is gone. Volumes mount a directory from your host (or a named Docker volume) into the container so data like a database survives restarts.

Registries (Docker Hub, ECR, GCR) store and distribute images. You push your built image there, and your production server or Kubernetes cluster pulls and runs it.

Minimal Dockerfile example

```
dockerfileFROM node:20-alpine  # base layer
WORKDIR /app
COPY package*.json ./          # copy deps manifest first (cache trick)
RUN npm ci                     # install deps as a cached layer
COPY . .                       # copy your app code
EXPOSE 3000
CMD ["node", "server.js"]
```

