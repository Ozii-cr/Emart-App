# Stage 1: Use an official Node.js image as the base image to build the artifact
FROM node:14 as nodeapi-build

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the entire application to the working directory
COPY ./ ./

# Install dependencies
RUN npm install

#Stage 2: Copy the artifact
FROM node:14

# Set the working directory in the container
WORKDIR /usr/src/app

#copy the artifact from the build stage
COPY --from=nodeapi-build /usr/src/app/ ./

# Expose the port the app runs on
EXPOSE 5000

# Define the command to run the application
ENTRYPOINT ["npm", "start"]
