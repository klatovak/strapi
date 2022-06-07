# Install dependencies only when needed
FROM node:16-alpine AS deps
# Check https://github.com/nodejs/docker-node/tree/b4117f9333da4138b03a546ec926ef50a31506c3#nodealpine to understand why libc6-compat might be needed.
RUN apk add --no-cache libc6-compat
WORKDIR /app

# Copy package manifests and install
COPY package*.json ./
RUN npm ci

# Copy build configuration
COPY tsconfig.json next.config.js next-env.d.ts .babelrc ./

USER node

EXPOSE 3000

WORKDIR /app/.next

WORKDIR /app

CMD ["npm", "run", "dev"]
