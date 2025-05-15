FROM node:18.17-alpine AS build

WORKDIR /home/app

COPY package*.json ./

RUN npm ci --only=production --legacy-peer-deps

# Install dependencies (including react-router-dom)
RUN npm install

COPY . .

FROM node:18.17-alpine

WORKDIR /home/app

COPY --from=build /home/app .

EXPOSE 5173

CMD ["npm", "run", "dev"]

