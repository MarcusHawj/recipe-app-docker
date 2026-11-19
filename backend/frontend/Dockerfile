# ---------- Stage 1: Build the frontend ----------
# Use the lightweight Node.js 18 Alpine image for the build stage
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json first so dependencies are cached
COPY package*.json ./

# Install the frontend's dependencies
RUN npm install

# Copy the rest of the frontend application files
COPY . .

# Build the production version of the app (outputs to /app/dist)
RUN npm run build

# ---------- Stage 2: Serve the built files with nginx ----------
# Use the lightweight nginx Alpine image to serve static files
FROM nginx:alpine

# Copy the built files from the first stage (stage 0) into nginx's web folder
COPY --from=0 /app/dist /usr/share/nginx/html

# Expose port 80, nginx's default port
EXPOSE 80

# Start nginx in the foreground so the container keeps running
CMD ["nginx", "-g", "daemon off;"]
