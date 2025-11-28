# Use official Node image
FROM node:18-alpine

# Set working directory
WORKDIR /usr/src/app

# Copy package files first (for better layer caching)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the code
COPY . .

# Expose backend port (change if backend uses different port)
EXPOSE 3000

# Use environment variable PORT or default 3000
ENV PORT=3000

# Start the app
CMD ["npm", "start"]
