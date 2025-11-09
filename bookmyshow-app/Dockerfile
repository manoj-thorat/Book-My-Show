# Use Node.js 18
FROM node:18

# Set working directory
WORKDIR /app

# Copy package files first
COPY package.json package-lock.json ./

# Fix postcss issue
RUN npm install postcss@8.4.21 postcss-safe-parser@6.0.0 --legacy-peer-deps

# Disable optional deps like fsevents (macOS-only)
ENV npm_config_optional=false

# Install chokidar (to prevent webpack crash)
RUN npm install chokidar@3 watchpack-chokidar2 --save-dev --legacy-peer-deps --force

# Install remaining dependencies safely
RUN npm install --legacy-peer-deps --force

# Copy source code
COPY . .

# Expose React app port
EXPOSE 3000

# Environment variables
ENV NODE_OPTIONS=--openssl-legacy-provider
ENV PORT=3000
ENV HOST=0.0.0.0

# Start application
CMD ["npm", "start"]
