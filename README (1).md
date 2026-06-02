# 🖧 GNS3 Labs — Topologies réseau

Ce dossier contient les topologies GNS3 utilisées pour **tester et valider** les configurations avant déploiement en production chez NAFTAL.

---

## 📐 Topologie principale — VPN 3 sites

```
                    ┌─────────────┐
                    │   INTERNET  │
                    │  (simulé)   │
                    └──────┬──────┘
           ┌───────────────┼───────────────┐
           │               │               │
    ┌──────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
    │  FortiGate  │ │  FortiGate  │ │  FortiGate  │
    │   Site 1    │ │   Site 2    │ │   Site 3    │
    └──────┬──────┘ └──────┬──────┘ └──────┬──────┘
           │               │               │
    ┌──────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
    │  Switch     │ │  Switch     │ │  Switch     │
    │  Cisco      │ │  Cisco      │ │  Cisco      │
    └──────┬──────┘ └──────┬──────┘ └──────┬──────┘
           │               │               │
    ┌──────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
    │  PC/Serveur │ │  PC/Serveur │ │  PC/Serveur │
    │  LAN-1      │ │  LAN-2      │ │  LAN-3      │
    └─────────────┘ └─────────────┘ └─────────────┘
```

---

## 🧪 Scénarios testés

| # | Scénario | Statut |
|---|----------|--------|
| 1 | VPN IPSec site-à-site entre 3 FortiGate | ✅ Validé |
| 2 | Filtrage ACL — blocage trafic entrant WAN | ✅ Validé |
| 3 | DHCP centralisé + relai DHCP | ✅ Validé |
| 4 | Routage inter-VLAN via FortiGate | ✅ Validé |
| 5 | Haute disponibilité (failover FortiGate) | 🔄 En cours |

---

## 🛠️ Matériel simulé dans GNS3

- **FortiGate VM** (image FortiOS 7.x)
- **Cisco IOSv** (routeurs et switches)
- **Linux** (serveurs DHCP, clients)
- **Cloud node** (connexion internet simulée)

---

## 📸 Captures d'écran

> Ajoute ici une capture d'écran de ta topologie GNS3 :
> `gns3-topo-3sites.png`

Pour exporter ta topo depuis GNS3 :
`File → Export portable project → .gns3project`

---

## 📝 Notes

- Toutes les configurations testées ici ont ensuite été déployées via Ansible en production
- Les images FortiGate ne sont pas incluses dans ce repo (licence Fortinet)
