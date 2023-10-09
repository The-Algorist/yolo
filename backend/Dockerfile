# Stage 1: Build the Node.js application
FROM node:alpine as builder

# Create a working directory within the container
WORKDIR /srv/app/admin-server

# Copy only the package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm ci --production --silent

RUN npm prune --production

# Copy the rest of the application files
COPY . .

# Build the application (if needed)
# RUN npm run build

# Stage 2: Create a minimal production image
FROM node:alpine

# Set the working directory within the container
WORKDIR /srv/app/admin-server

# Copy the application files and dependencies from the builder stage
COPY --from=builder /srv/app/admin-server ./

# Expose the port on which your backend server is listening (e.g., 5000)
EXPOSE 5000

# Start the backend application
CMD ["npm", "start"]               


