#Stage 1: Use an official OpenJDK image as the base image to build the artifact
FROM openjdk:8 as build

# Set the working directory in the container
WORKDIR /usr/src/app

# Download and install Maven dependencies
RUN apt update && apt install -y maven 

# Copy the entire application to the working directory
COPY ./ ./

# Build the Java application while skipping the tests
RUN mvn install -Dskiptests

#Stage 2: Copy the artifact
FROM openjdk:8 

# Set the working directory in the container
WORKDIR /usr/src/app

#copy the artifact from the build stage
COPY --from=build /usr/src/app/target/book-work-0.0.1-SNAPSHOT.jar ./book-work-0.0.1.jar


# Expose the port the API will run on
EXPOSE 9000

#  command to run the Java application
ENTRYPOINT ["java", "-jar", "book-work-0.0.1.jar"]
