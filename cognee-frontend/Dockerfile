# Use an official Node.js runtime (Debian-based to avoid musl/lightningcss issues)
FROM node:22-slim

# Set the working directory to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package.json package-lock.json ./

# Install any needed packages specified in package.json
RUN npm ci

# Copy the rest of the application code to the working directory
COPY src ./src
COPY public ./public
COPY next.config.mjs .
COPY postcss.config.mjs .
COPY tsconfig.json .

# Build the app
RUN npm run build

# Expose port 3000
EXPOSE 3000

# Start the app in production mode
CMD ["npm", "start"]
