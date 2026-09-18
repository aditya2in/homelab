# 📦 Manifests

Kubernetes manifests, organised **one folder per capability** (maps to the CKAD capability map).

```text
manifests/capabilities/
├── cap-01-pod/
├── cap-02-deploy/
├── cap-03-service/
├── cap-04-config/
├── cap-05-probes/
├── cap-06-ingress/
├── cap-07-netpol/
├── cap-08-storage/
├── cap-09-rbac/
└── cap-10-diagnose/
```

Each folder holds the manifests built cold for that capability, plus any chaos/breakage variants used for the "Break & Fix" drill.
