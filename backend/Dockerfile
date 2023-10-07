#Using a node alpine image
FROM node:alpine3.18

# setting the working directory

# Copying the package.json file to the working directory
COPY package*.json ./

# Installing the dependencies
RUN npm install

# Copying the resr of the files to the working directory
COPY . .

# Exposing the port 3000
EXPOSE 3000

# Running the app
CMD ["npm", "start"]
