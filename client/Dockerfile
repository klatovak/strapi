# Install dependencies only when needed
FROM node:16-alpine AS deps

RUN apk add --no-cache tini
ENTRYPOINT [ "tini", "-g", "--" ]

# Check https://github.com/nodejs/docker-node/tree/b4117f9333da4138b03a546ec926ef50a31506c3#nodealpine to understand why libc6-compat might be needed.
RUN apk add --no-cache libc6-compat

WORKDIR /app

RUN chown -R node:node /app

# Copy package manifests and install
COPY package*.json ./

RUN npm ci

USER node

EXPOSE 3000

CMD ["npm", "run", "dev"]
