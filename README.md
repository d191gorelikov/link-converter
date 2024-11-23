# Personal Link Conversion Project

This is a personal project that is a backend application for link conversion with automated deployment via Helm and Kubernetes. It consists of several components:

- **Core application** for link processing.
- **CI/CD configurations** for automatic build, testing, and deployment.
- **Helm chart** for deploying the application and PostgreSQL database.

## Key Features:

- Docker image build using Kaniko.
- Integration with SAST for security during the testing phase.
- Automated deployment with Helm.
- Configuration parameters stored in Kubernetes secrets.

The project uses **PostgreSQL** as the database, and all configuration parameters, including database credentials, are securely stored in Kubernetes secrets.


![image](https://github.com/user-attachments/assets/5c595a5b-9834-492b-9433-11865c5f8de3)


This application will generate short link for you

## How to build without Helm

1. Install Java 11 or higher, Maven 3 and Docker
2. Build the project:
```shell
mvn clean package
```

## How to start

1. Start Postgres 13 use Docker
```shell
docker run -p port:5432 -e POSTGRES_PASSWORD=<password> -it --rm postgres:13
```
2. Add to env all required variables to connect to the DB:
DB_HOST, DB_PORT, DB_NAME, DB_LOGIN, DB_PASSWORD
3. Start the application:
```shell
java -jar target/*.jar

