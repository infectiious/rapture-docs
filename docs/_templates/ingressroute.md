# Ingressroute Templates.
!!! danger "Reminder"
    Please don't forget to replace the below 🤠

    *{{ namespace }}*  
    *{{ hostname }}*  

```
      apiVersion: traefik.containo.us/v1alpha1
      kind: IngressRoute
      metadata:
        name: traefik-dashboard
        namespace: {{ namespace }}
      spec:
        entryPoints:
          - web
          - websecure
        routes:
          - match: Host(`{hostname}`) # Hostname to match.
            kind: Rule
            services: # Service to redirect requests to.
              - name: api@internal
                kind: TraefikService
            # Middlewares NOT REQUIRED.
            middlewares:
              - name: auth
        # Use the secret generated by cert-manager
        tls:
          secretName: {{ hostname }}
```

---