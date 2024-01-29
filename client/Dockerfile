#Stage 1: Build the AngularJS application
FROM node:14 as builder

#set the working directory 
WORKDIR /usr/src/app

# Copy the entire application to the working directory
COPY ./ ./

# Install dependencies and build the artifact
RUN npm install && npm run build --prod

#Stage 2: Serve the application using Nginx
FROM nginx:latest

# Copy the built AngularJS application from the builder 
COPY --from=builder /usr/src/app/dist/client /usr/share/nginx/html

# Copy the Nginx configuration file
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose the port the app runs on
EXPOSE 4200

