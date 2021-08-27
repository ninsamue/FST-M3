# Base Image
FROM node:alpine as builder
 
# Change workdir to '/app'
WORKDIR '/app'
 
# Copy package.json into the
# container
COPY package.json .
 
# Install dependencies
RUN npm install
 
# Copy the rest of the files
# into the container
COPY . .
 
# Build the production files
CMD ["npm", "run", "build"]


# Run Phase
FROM node:alpine
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY --from=builder /app/dist .
CMD ["node", "./dist/server.js"]