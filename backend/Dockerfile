# Use the lightweight Node.js 18 Alpine image as the base
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json first so dependencies are cached
COPY package*.json ./

# Install the backend's dependencies
RUN npm install

# Copy the rest of the backend application files
COPY . .

# Create a directory to store the SQLite database file
RUN mkdir -p /app/data

# Expose port 5000, the port the backend API runs on
EXPOSE 5000

# Start the backend server
CMD ["npm", "start"]
