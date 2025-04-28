# Stage 1: Build
FROM node:14 AS build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .
# Stage 2: Production
FROM node:14-slim AS production

WORKDIR /app

# Copy only the necessary files from the build stage
COPY --from=build /app /app

# Optionally, prune devDependencies (if you used npm ci or separated them)
RUN npm prune --production

CMD [ "npm", "start" ]
