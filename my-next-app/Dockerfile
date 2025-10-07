# ===== Stage 1 — Dependencies =====
FROM node:18-alpine AS deps
WORKDIR /app
COPY package*.json ./
RUN npm ci

# ===== Stage 2 — Builder =====
FROM node:18-alpine AS builder
WORKDIR /app
COPY . .
COPY --from=deps /app/node_modules ./node_modules
RUN npm run build

# ===== Stage 3 — Runner =====
FROM node:18-alpine AS runner
WORKDIR /app

ENV NODE_ENV=production

# Copy only what’s needed for production
COPY --from=builder /app/.next ./.next
COPY --from=builder /app/public ./public
COPY --from=builder /app/package.json ./package.json
COPY --from=builder /app/node_modules ./node_modules

EXPOSE 3000

CMD ["npm", "start"]