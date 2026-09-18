# 🧱 Cluster Configuration

Version-controlled, sanitised cluster configuration.

| Folder | Contents |
| :--- | :--- |
| `kubeadm/` | `kubeadm init` / `join` configs (tokens removed) |
| `cri/` | `containerd` configuration |
| `cni/` | Flannel manifests / Helm values |
| `ha/` | HAProxy + Keepalived for the VIP |

> ⚠️ Never commit real join tokens, certificates, or kubeconfigs. Use placeholders like `<TOKEN>` and `<CA-CERT-HASH>`.
