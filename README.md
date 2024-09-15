# Kube Project

This project sets up a Kubernetes environment with Nginx, PHP-FPM, and MySQL using Persistent Volumes.

## Prerequisites

- Kubernetes cluster
- `kubectl` configured to interact with your cluster

## Deployment

1. **Create Persistent Volume and Persistent Volume Claim:**

    ```sh
    kubectl apply -f app-pvc.yaml
    ```

2. **Deploy PHP-FPM:**

    ```sh
    kubectl apply -f php-fpm.yaml
    ```

3. **Deploy Nginx:**

    ```sh
    kubectl apply -f nginx.yaml
    ```

4. **Deploy MySQL:**

    ```sh
    kubectl apply -f mysql.yaml
    ```

## Usage

- Access the Nginx service via NodePort on port `30080`.
- Nginx will serve content from the Persistent Volume and pass PHP requests to PHP-FPM.

## Configuration

- **Nginx ConfigMap:** Modify `nginx.yaml` to change Nginx configuration.
- **Persistent Volume:** Ensure the path `/var/website` exists on the host for the Persistent Volume.

## Cleanup

To delete all resources created by this project:

```sh
kubectl delete -f nginx.yaml
kubectl delete -f php-fpm.yaml
kubectl delete -f mysql.yaml
kubectl delete -f app-pvc.yaml