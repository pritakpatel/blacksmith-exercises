FROM node:22-bookworm-slim

WORKDIR /app
RUN apt-get update && apt-get install -y python3 make g++ && rm -rf /var/lib/apt/lists/*

COPY app/scripts/docker-build-workload.js ./scripts/
RUN node scripts/docker-build-workload.js

COPY app/package.json app/package-lock.json ./
RUN npm ci --omit=dev

COPY app ./

EXPOSE 3000

CMD ["node", "src/server.js"]
