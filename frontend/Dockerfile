# ----------- Build stage -----------
FROM node:20-alpine AS builder

WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy source code
COPY . .

# Build Next.js app
RUN npm run build


# ----------- Production stage -----------
FROM node:20-alpine

WORKDIR /app

ENV NODE_ENV=production

# Copy everything from builder
COPY --from=builder /app ./

EXPOSE 3000

# Start Next.js
CMD ["npm", "start"]
