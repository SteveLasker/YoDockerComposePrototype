# Image with the latest Node.js
FROM node

# Create a /src folder.
RUN mkdir /src

# Add the contents of the project folder to the /src folder
ADD . /src

# Set the working directory.
WORKDIR /src

# Expose the port on the container.
EXPOSE 3000


# Install the dependencies.
RUN npm install

# Run the app.
CMD ["node", "./bin/www"]