# Kubernetes Multi-Service Architecture

## 1. Creating the Pods and Services

### NGINX Pod
- Created a `nginx-pod.yml` file that defines the NGINX pod.
- The pod runs an NGINX container with a simple web server configuration.

### Redis Pod
- Created a `redis-pod.yml` file that defines the Redis pod.
- The pod runs a Redis container for in-memory data storage.

### NGINX Service
- Created a `nginx-service.yml` file to expose the NGINX pod using a NodePort service.
- This allows external access to the NGINX web server.

### Redis Service
- Created a `redis-service.yml` file to expose the Redis pod using a ClusterIP service.
- This service is internal and allows only in-cluster communication.

## 2. Ensuring Front-End and Back-End Communication

- Modified the NGINX configuration to pull data from the Redis service using the ClusterIP.
- Verified that the NGINX web server could successfully retrieve and display data from Redis.

## 3. Testing and Verification

- Used `kubectl get pods` and `kubectl get services` to verify that all pods and services were running as expected.
- Accessed the NGINX service via the NodePort to ensure that it displayed data from the Redis service correctly.

## 4. Challenges Faced and Resolutions

- **Issue:** Faced issues with the Redis pod not starting correctly due to a misconfiguration in the `redis-pod.yml` file.
  - **Resolution:** Corrected the configuration and re-applied the pod using `kubectl apply -f redis-pod.yml`.

- **Issue:** NGINX was initially unable to communicate with Redis due to a typo in the service name.
  - **Resolution:** Fixed the typo in the NGINX configuration and re-deployed the service.

## Conclusion

This project demonstrates how to deploy a multi-service architecture in Kubernetes, including creating and configuring services for inter-service communication. The NGINX front-end successfully interacts with the Redis back-end service, reinforcing key concepts of Kubernetes service management.
