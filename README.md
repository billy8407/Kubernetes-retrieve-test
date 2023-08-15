# Kubernetes-retrieve-test

Here's a step-by-step guide:

1. **Create a YAML File (e.g., `curl-pod.yaml`):**
    
    Create a YAML file that describes a Kubernetes Pod running a container with the **`curl`** tool.
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: curl-pod
      namespace: default
    spec:
      containers:
      - name: curl-container
        image: curlimages/curl:latest
        command: ["sleep", "infinity"]
    
    ```
    
2. **Apply the YAML File:**
    
    Apply the YAML file to create the Pod:
    
    ```bash
    kubectl apply -f curl-pod.yaml
    
    ```

    
3. **Access the Pod:**
    
    Access the Pod using **`kubectl exec`**:
    
    ```bash
    kubectl exec -it curl-pod -- /bin/sh
    
    ```

4. **Use the kubectl proxy Command:**
    
    It creates a proxy server between your local machine and the Kubernetes API server. This will handle the SSL connection and authentication for you.
    ```bash
    kubectl proxy

    ```

5. **Use `curl` Inside the Pod:**
    
    Inside the Pod shell, you can use the **`curl`** command to retrieve information about other Pods in the **`default`** namespace. For example, you can retrieve a list of Pods using:
    
    ```bash
    curl http://localhost:8001/api/v1/namespaces/default/pods
    
    ```
    
    Please note that the Kubernetes API server is available at **`localhost:8001`** within the Pod.