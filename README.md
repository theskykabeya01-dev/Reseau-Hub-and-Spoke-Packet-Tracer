# Reseau-Hub-and-Spoke-Packet-Tracer
Conception réseau Hub-and-Spoke multi-sites - Packet Tracer - VLAN, Router-on-a-Stick, Routage Statique

## 🎓 Contexte du Projet
Projet de défense - Conception et simulation d'un réseau d'entreprise multi-sites.

Un site central (Hub) qui centralise les services, relié à 2 sites distants (Spokes) via un cœur de réseau simulant Internet (ISP).

## 🏗️ Architecture

### 1. Le Hub (Site Central)
- **10 Départements** : VLAN 10 à VLAN 100
- **1 Serveur de stockage** : VLAN 110
- Routage Inter-VLAN par Router-on-a-Stick

### 2. Les Spokes (Sites Distants)
- **Spoke 1** : 3 Départements
- **Spoke 2** : 3 Départements
- Chaque site a son propre routeur + switch

### 3. L'ISP (Cœur de Réseau)
- Routeur central qui simule Internet
- Assure l'interconnexion Hub <-> Spokes

## 🗺️ Plan d'Adressage IP

| Site | Plage IP | Description |
| :--- | :--- | :--- |
| **Hub** | `172.16.10.0` à `172.16.110.0` | 10 VLANs + Serveur |
| **Spoke 1 & 2** | `172.16.1.0` à `172.16.6.0` | 3 VLANs par site |
| **WAN / ISP** | `10.0.0.x` | Liaisons entre routeurs |

## ⚙️ Équipements Configurés (7)

- **3 Routeurs** : Hub, Spoke 1, Spoke 2
    - Sous-interfaces pour le routage Inter-VLAN
    - Route par défaut vers l'ISP
- **3 Switches** : Hub, Spoke 1, Spoke 2
    - Création des VLANs
    - Ports Access pour les départements
    - Ports Trunk vers les routeurs
- **1 Routeur ISP**
    - Routes de retour vers le Hub et les Spokes

## 🧪 Tests de Connectivité Validés

1.  **Layer 2** : PC VLAN 10 -> Passerelle `172.16.10.1`
2.  **Inter-VLAN** : VLAN 10 -> VLAN 20 sur le Hub
3.  **WAN** : Hub / Spokes -> ISP `10.0.0.2`
4.  **Hub <-> Spoke** : PC Hub -> `172.16.1.1` (Spoke)
5.  **Bout en bout** : PC VLAN 10 Hub -> PC VLAN 1 Spoke 1

## 🛠️ Technologies Utilisées
- Cisco Packet Tracer
- VLAN, Trunk 802.1Q, Router-on-a-Stick
- Routage Statique
- Adressage IPv4

## 📁 Fichiers
- `Hub-and-Spoke.pkt` : Fichier Packet Tracer complet
- `/docs/` : Captures d'écran des tests ping
