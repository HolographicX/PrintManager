FROM node:current-alpine AS build

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to install dependencies first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the React app files
COPY . . 

# Build the React app for production
RUN npm run build

# Simple static file server to serve the built React app
FROM nginx:alpine

# Copy the built React app into the nginx directory
COPY --from=build /usr/src/app/build /usr/share/nginx/html

# Expose port 80 (default for nginx)
EXPOSE 80

# Start nginx server
CMD ["nginx", "-g", "daemon off;"]
