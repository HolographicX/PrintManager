FROM node:current-alpine

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to install dependencies first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the server files
COPY . . 

# Expose the port the server will run on
EXPOSE 3001

# Start the server
CMD ["npm", "start"]
