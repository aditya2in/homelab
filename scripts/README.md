# 🛠️ Scripts

Automation for the homelab.

Suggested contents (built incrementally):

- `bootstrap-node.sh` — pre-kubeadm host prep (swap, modules, sysctl)
- `cluster-health.sh` — node/pod/etcd health snapshot
- `etcd-backup.sh` — scheduled etcd snapshot
- `join-print.sh` — generate a fresh join command

> Secrets (tokens, keys) must never be hardcoded — read from files excluded by `.gitignore` or from the environment.
