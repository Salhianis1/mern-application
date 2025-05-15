FROM node:18.17-alpine AS build

WORKDIR /home/app

COPY package*.json ./

# Install build tools needed by some npm packages
RUN apk add --no-cache python3 make g++

RUN npm ci --only=production --legacy-peer-deps

COPY . .

FROM node:18.17-alpine

WORKDIR /home/app

COPY --from=build /home/app .

EXPOSE 5173

CMD ["npm", "run", "dev"]

