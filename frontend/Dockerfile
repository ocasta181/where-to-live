# syntax=docker/dockerfile:1

# Base image for both development and production
FROM node:20-slim as base

# Set working directory
WORKDIR /app

# Development stage
FROM base as development

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Production stage
FROM base as production

# Copy package files
COPY package*.json ./

# Install production dependencies
RUN npm ci --only=production

# Copy application code
COPY . .

# Build the application
RUN npm run build

# Use nginx to serve the built application
FROM nginx:alpine as nginx

# Copy built files to nginx
COPY --from=production /app/dist /usr/share/nginx/html

# Copy nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
