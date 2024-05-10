# Use an official Node runtime as a base image
FROM node:20.13.0

# Set the working directory in the container to /app
WORKDIR /app

RUN npm cache clean --force
# Copy the package.json and package-lock.json (or yarn.lock) to install dependencies
COPY package*.json yarn.lock ./

# Install project dependencies
RUN npm install --legacy-peer-deps

# Bundle app source
COPY . .

# Set NODE_OPTIONS environment variable
ENV NODE_OPTIONS="--openssl-legacy-provider"

# Build the React application
RUN npm run build

# Install serve to serve the build directory
RUN npm install -g serve

# Make port 3000 available to the outside world
EXPOSE 3000

# Define environment variable
ENV NAME World

# Run serve to serve the static build directory
CMD ["serve", "-s", "build", "-l", "3000"]
