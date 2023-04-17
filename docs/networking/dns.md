# Certificate template

### Replace:

```yaml
  - {{ name }}
  - {{ namespace }}
  - {{ dns-name }}
```

```yaml
---
apiVersion: cert-manager.io/v1
kind: Certificate
metadata:
  name: {{ name }}
  namespace: {{ namespace }}
spec:
  secretName: {{ name }}
  issuerRef:
    name: acme-issuer
    kind: ClusterIssuer
  dnsNames:
    - {{ dns-name }}
```
