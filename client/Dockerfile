# FROM node:18-alpine
# WORKDIR /app
# COPY package*.json ./
# RUN npm install
# COPY . .
# EXPOSE 3000

# CMD ["npm", "start"]

# Tahap 1: Build (Memasak Code)
FROM node:18-alpine as builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# Tahap 2: Serve dengan Nginx (Menghidangkan)
FROM nginx:alpine
# Copy hasil build dari Tahap 1 ke folder Nginx
COPY --from=builder /app/build /usr/share/nginx/html
# Expose port 80 (Standard Web)
EXPOSE 80
# Jalankan Nginx
CMD ["nginx", "-g", "daemon off;"]