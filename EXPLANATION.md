**Choice of Image:**

**For the backend side:** I chose to use a _ **node:alpine** _ images the builder image: this is due to it's small size and low to 0 vulnerabilities. I also used the same to create a production image in the stage 2 of the build. The backend also runs a node server hence influencing the choice of image. _ **Image size is 270mb** _. It could however be reduced further.

**For the client side:** I chose to use _ **node 18** _ **:** as build image. This is so as to compile the modules and packages and build them. I then went ahead to use _ **nginx:alpine** _ as the production image. The nginx:alpine is small and lightweight and quite secure thus bringing the final client image to a mere _ **69.5mb** 

![Alt text](<explanation images/Image-sizes.png>)


**Dockerfile directives used in the creation and running of each container.**

I used a _ **multi-stage build** _ strategy to build both images. I will generally list and minimally explain the commands here (they are well commented in the respective files)

**Client**

```dockerfile

FROM baseImage as build
WORKDIR /app
COPY package\*.json ./
RUN npm install
COPY . .
RUN npm run build
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
RUN sed -i 's/80/3000/g' /etc/nginx/conf.d/default.conf
EXPOSE 3000
CMD ["nginx", "-g", "daemon off;"]

```

**Backend**

```dockerfile

# Stage 1: Build the Node.js application
FROM node:alpine as builder
# Create a working directory within the container
WORKDIR /srv/app/admin-server
# Copy only the package.json and package-lock.json files
COPY package\*.json ./
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

```

**Docker-compose Networking (Application port allocation and a bridge network implementation) where necessary.**

- given that the application contains a client and a backend container, they both need to be in communication thus I used a custom network built

**Docker-compose volume definition and usage (where necessary).**

I added a volume to the backend container for persistence

**Git workflow used to achieve the task.**

- Forking the Repo as required by the instructions
- Cloning into the repo
- Running the npm install in both client and backend environments to update package files
- Commiting the changes to the package files
- Running npm start to test if the app is working on local
- Adding and committing dockerfiles added to both client and backend
- Consistenly pushing changes to the repo as per local dev changes
- Iterating through the adding, committing and pushing process as I create and make changes to the local dev environment
- Adding sensible and well written commit messages for every staged and pushed commit

**Successful running of the applications and if not, debugging measures applied.**

The backend container run successfully on first attempt hence I pushed a v1.0.0 image to dockerhub as the first production ready version for yolo-backend

The client container needed updates in some files so I used the error messages to debug and fix the file during the multi-stage build and reduction strategies. I ended up having 2 versions. The versions are all tagged and deployed to dockerhub.

**Good practices such as Docker image tag naming standards for ease of identification of images and containers.**

_I used semver versioning principles:_

_Assuming a tag X.Y.Z ; X represents the major version increment, Y represents a minor version increment, z represents the patch version increments_

 **There is a screenshot of mydeployed images on DockerHub, clearly showing the versions of the images**
 *client*
 ![Alt text](<explanation images/yolo-client.png>)

 *backend*
![Alt text](<explanation images/yolo-backend.png>)