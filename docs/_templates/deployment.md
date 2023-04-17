# Deployment Templates.

!!! danger "Reminder"
    Please don't forget to replace the below 🤠

    *{{ name }}*  
    *{{ namespace }}*  
    *{{ image }}*  
    *{{ tag }}*  
    *{{ mount-path }}*  
    *{{ volumename }}*  
    *{{ pvc-name }}*  
    *{{ claim-name }}*  

```yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ name }}
  namespace: {{ namespace }}
  labels:
    app: {{ name }}
spec:
  selector:
    matchLabels:
      app: {{ name }}
  replicas: 1
  strategy:
    type: Recreate
  template:
    metadata:
      labels:
        app: {{ name }}
    spec:
      containers:
        - name: {{ name }}
          image: {{ image }}:{{ tag }}
          resources: {}
          # resources:
          #   limits:
          #     memory: 512Mi
          #     cpu: "1"
          #   requests:
          #     memory: 256Mi
          #     cpu: "0.2"
          ports:
            - containerPort: 8080
          # env:
          #   - name: name
          #     value: value
          volumeMounts:
            - mountPath: {{ mount-path }}
              name: {{ volumename }}
      volumes:
        - name: {{ pvc-name }}
          persistentVolumeClaim:
            claimName: {{ claim-name }}
status: {}
```

---
