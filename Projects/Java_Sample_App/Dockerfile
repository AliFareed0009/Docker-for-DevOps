# Pull Base Image which gives all required tools and libraries ( image_name:tag )
FROM openjdk:17-jdk-alpine

# metadata
LABEL maintainer="your-email@example.com"
LABEL version="1.0"
LABEL description="A simple Java application"

# Create a Folder /app where code will be stored
WORKDIR /app

# Copy the source code form HOST machine to your container ( In this case from /src to /app )
COPY src/Main.java /app/Main.java

# Compile java application code with javac
RUN javac Main.java

# Run the Application
CMD [ "java", "Main" ]