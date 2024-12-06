# Pulling Base Image Node Version 20
FROM node:20

# Creating Working Directory /webapp
WORKDIR /webapp

# Copying Code From Reac_Web_App to container folder /webapp
COPY . .

# Install Node Package Modules npm
RUN npm install

# Exposing the Port 3000 in the container ( This means the Application will run on port 3000 in the container )
EXPOSE 3000

# Run the Application
CMD [ "npm", "start" ]