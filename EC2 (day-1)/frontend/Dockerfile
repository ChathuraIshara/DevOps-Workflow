FROM node:20-alpine

WORKDIR /frontend

# Copy dependency files first (better caching)
COPY package.json package-lock.json* ./

# Install fresh dependencies
RUN npm ci

# Install serve globally
RUN npm install -g serve

# Copy rest of the code
COPY . .

# Rebuild esbuild for Alpine (important!)
RUN npm rebuild esbuild

# Build React app
RUN npm run build

EXPOSE 3000

# Serve the build
CMD ["serve", "-s", "dist", "-l", "3000"]
