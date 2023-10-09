# Stage 1: Build the client application
FROM node:alpine3.18 as builder

# Set the working directory within the container
WORKDIR /srv/app/admin-client

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install all dependencies (including dev dependencies)
RUN npm install

# Copy the source code to the container
COPY src ./src
COPY public ./public

# Build the client application (customize the build command if needed)
RUN npm run build

# Stage 2: Create a minimal production image
FROM nginx:alpine

# Copy the build artifacts from the builder stage into the NGINX web root
COPY --from=builder /srv/app/admin-client/build /usr/share/nginx/html
RUN sed -i 's/80/3000/g' /etc/nginx/conf.d/default.conf

COPY proxy.config /etc/nginx/conf.d/default.conf

# Expose port 3000 for the NGINX server
EXPOSE 3000


# Start NGINX when the container runs
CMD ["nginx", "-g", "daemon off;"]



