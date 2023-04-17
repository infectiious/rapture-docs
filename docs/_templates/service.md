# Service Templates.

## Standard Service.

!!! danger "Reminder"
    Please don't forget to replace the below 🤠

    *{{ servicename }}*  
    *{{ namespace }}*  
    *{{ appname }}*  

```yaml
---
apiVersion: v1
kind: Service
metadata:
  name:  {{ servicename }}
  namespace: {{ namespace }}
spec:
  selector:
    app:  {{ appname }}
  # ---
  # Service to use with Traefik Ingress
  # ports:
  # - name:  http
  #   port:  8080
  #   targetPort: 80
  #   protocol: TCP  # optional protocol
  # type:  ClusterIP
  # ---
  # ClusterIP means this service can be accessed by any pod in the cluster
  # ports:
  # - name:  http
  #   port:  8080
  #   targetPort: 80
  #   protocol: TCP  # optional protocol
    # type:  Traefik Ingress Service
  # type:  ClusterIP
  # ---
  # NodePort means this service is only accessible by pods in the same namespace
  # ports:
  # - name:  http
  #   port:  80
  #   nodePort: 30001
  #   protocol: TCP  # optional protocol
  # type:  NodePort
  # ---
  # LoadBalancer means this service is load-balanced across all nodes in the cluster
  # ports:
  # - name:  http
  #   port:  80
  #   targetPort: 30001
  #   protocol: TCP  # optional protocol
  # type:  LoadBalancer
```

---

## External-DNS Service.

!!! danger "Reminder"
    Please don't forget to replace the below 🤠

    *{{ name }}*  
    *{{ namespace }}*  
    *{{ hostname }}*  

```yaml
---
apiVersion: v1
kind: Service
metadata:
  name: {{ name }}
  namespace: {{ namespace }}
spec:
  selector:
    app: {{ name }}
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
---
apiVersion: v1
kind: Service
metadata:
  name: {{ name }}
  annotations:
    external-dns.alpha.kubernetes.io/hostname: {{ hostname }}
spec:
  type: ExternalName
  externalName: 10.0.0.204
```

---
