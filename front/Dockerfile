# Utilisation de l'image de base Node.js
FROM node:alpine AS buil-step

# Définit le répertoire de travail
WORKDIR /app

# Copie le fichier package.json et package-lock.json
COPY package*.json /app

# Installe les dépendances
RUN npm install

# Copie le reste des fichiers de l'application
COPY . /app

# Compile l'application Angular en mode de production
RUN npm run build -- --outputPath=./dist/out

# Utilise une image Nginx
FROM nginx as prod

# Copie les fichiers de l'application compilée dans le répertoire approprié
COPY --from=build-step /app/dist/out/ /usr/share/nginx/html/