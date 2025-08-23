#------------Step-1: Build the application using Node.js-----------
FROM node:20-alpine AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory 
# This allows Docker to cache the npm install step
COPY package*.json ./

# Install dependencies
# This will only run if package.json or package-lock.json changes
RUN npm install 

# Copy the rest of the application code to the working directory
COPY . .

# Build the application
# This will create the production-ready files in the dist directory
RUN npm run build


#------------Step-2: Serve the application using Nginx--------------
FROM nginx:alpine

# Remove the default Nginx static files
# This ensures that the Nginx server serves our built application files
RUN rm -rf /usr/share/nginx/html/*

# Copy the Nginx configuration file
# This file should be configured to serve the static files from the dist directory
COPY ./frontend/nginx.conf /etc/nginx/conf.d/default.conf

# Copy the built application files from the builder stage to the Nginx html directory
# This allows Nginx to serve the static files
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port 80
# This is the default port for Nginx to serve HTTP traffic
EXPOSE 80

# Start Nginx in the foreground
# This keeps the container running and allows it to serve requests
CMD ["nginx", "-g", "daemon off;"]

