# Ingress Templates.

## Default Ingress

```yaml
---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: ingress
  namespace: namespace
spec:
  rules:
  - host: "your-hostname.com"
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: your-service-name
            port:
              number: 80
```

---

## Traefik Ingress
```yaml
---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: wp-clcreative
  namespace: wp-clcreative
  # annotations:
  #   (Optional): Annotations for the Ingress Controller
  #   ---
  #   General:
  #   kubernetes.io/ingress.class: traefik

  #   TLS configuration:
  #   traefik.ingress.kubernetes.io/router.entrypoints: web, websecure
  #   traefik.ingress.kubernetes.io/router.tls: "true"

  #   Middleware:
  #   traefik.ingress.kubernetes.io/router.middlewares:your-middleware@kubernetescrd
spec:
  rules:
  - host: "your-hostname.com"  # Your hostname
    http:
      paths:
      # Path-based routing settings:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: your-service-name  # The name of the service
            port:
              number: 80  # Service Portnumber
  # tls:
  # - hosts:
  #   - your-hostname.com  # Your hostname
  #   secretName: your-secret  # Your TLS Secret
```

---
