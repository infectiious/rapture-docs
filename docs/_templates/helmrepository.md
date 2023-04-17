# Helm Repository Templates.

!!! danger "Reminder"
    Please don't forget to replace the below 🤠

    *{{ chart-url }}*  


```yaml
---
apiVersion: source.toolkit.fluxcd.io/v1beta2
kind: HelmRepository
metadata:
  name: external-dns-charts
  namespace: flux-system
spec:
  interval: 1h
  url: {{ chart-url }}
```

---
