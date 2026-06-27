FROM node:20-alpine

# Installer pnpm
RUN npm install -g pnpm

WORKDIR /app
COPY . .

# Installer les dépendances du monorepo (à la racine)
RUN pnpm install

# Build l'API
RUN cd api && pnpm run build

# Copier start.sh et le rendre exécutable
COPY start.sh .
RUN chmod +x start.sh

# Installer caddy
RUN apk add --no-cache caddy

CMD ["./start.sh"]
