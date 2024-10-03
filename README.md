
# Vprofile - Java Web Application Project Using Kubernetes

## Project Overview

Vprofile is a Java-based web application designed to demonstrate the concepts of container orchestration using Kubernetes. The application consists of multiple services, including a Tomcat application server,
MySQL database, RabbitMQ message broker, and Memcached cache. This project aims to provide a comprehensive understanding of managing a full web application in a Kubernetes environment.

## Technologies Used

- **Java**: Main programming language for the application.
- **Tomcat**: Application server for deploying the Java application.
- **MySQL**: Relational database for data storage.
- **RabbitMQ**: Message broker for asynchronous communication.
- **Memcached**: In-memory caching system for improved performance.
- **Kubernetes**: Container orchestration platform for managing the application services.

## Setup Instructions

### Prerequisites

- Kubernetes cluster (Minikube)
- `kubectl` command-line tool installed
- Docker installed (for building images)

### Steps to Deploy

1. **Create a Namespace**:
   ```bash
   kubectl create namespace vpro-ns
   ```

2. **Create Persistent Volume (PV) and Persistent Volume Claim (PVC)**:
   - Create the PV and PVC for the MySQL database:
   ```bash
   kubectl apply -f dbpv.yml
   ```

3. **Create Secrets for Database and RabbitMQ Credentials**:
   ```bash
   kubectl apply -f vprocret.yml
   ```

4. **Deploy MySQL Database**:
   ```bash
   kubectl apply -f vprodb.yml
   ```

5. **Deploy Memcached**:
   ```bash
   kubectl apply -f vpromc.yml
   ```
 6. **Create config map**:
 ```bash
 kubectl apply -f vprocm.yml
 ```

7. **Deploy RabbitMQ**:
   ```bash
   kubectl apply -f vprormq.yml
   ```

78. **Deploy the Java Application**:
   ```bash
   kubectl apply -f vproapp.yml
   ```

### Accessing the Application

After deploying the application, you can access it using the NodePort specified in the service configuration. Use the following command to get the list of services and find the port:

```bash
kubectl get services -n vpro-ns
```

## Troubleshooting

- **Pending PVC**: Ensure that the PV and PVC are correctly configured. Check for typos or misconfigurations in the YAML files.
- **Init Container Issues**: Verify the commands used in the init containers to ensure they are correctly waiting for services to start.

## Contributing

If you would like to contribute to the project, please feel free to submit a pull request or open an issue.

## Acknowledgments

- Inspired by Kubernetes documentation and community resources.
- Thanks to contributors who provided feedback and support.

