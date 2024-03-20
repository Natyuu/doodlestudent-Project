# Étape de construction
FROM maven:3.8.4-openjdk-11-slim AS build-step

# Définit le répertoire de travail
WORKDIR /app

# Copie le code source dans le conteneur
COPY . .

# Construit l'application avec Maven
RUN mvn package -Dmaven.test.skip=true

# Étape de production
FROM openjdk:11-jre-slim

# Copie le jar de l'étape de construction dans le conteneur
COPY --from=build-step /app/target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar /app/

# Expose le port 8080
EXPOSE 8080

# Commande pour démarrer l'application
CMD ["java", "-jar", "/app/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar"]