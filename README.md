# TP MPLS / VPN L3 - Configuration GNS3

Ce dépôt regroupe la configuration et la documentation d'un TP de réseaux portant sur la mise en place d'un réseau privé virtuel de niveau 3 (**L3VPN**) basé sur une architecture **MPLS** (Multi-Protocol Label Switching) sous GNS3.

---

## 📌 Objectifs du TP
* **Isolation du trafic client :** Configuration des VRF (Virtual Routing and Forwarding) sur les routeurs Provider Edge (PE).
* **Cœur de réseau opérateur :** Activation du routage MPLS et distribution des étiquettes via le protocole **LDP** (Label Distribution Protocol).
* **Validation de bout en bout :** Test de connectivité (VPN L3) entre le site distant (Siège) et l'agence à travers le cloud opérateur.

---

## 🛠️ Topologie et Rôles des Équipements
1. **`sp1` (PE d'entrée) :** 
   * Création de la VRF `Client_A` (RD `100:1`, RT `100:1`).
   * Association de l'interface connectée au réseau client (`FastEthernet0/0`).
2. **`sp2` (Routeur Cœur / P) :** 
   * Activation globale de MPLS (`mpls ip`, `mpls label protocol ldp`).
   * Activation de MPLS sur les interfaces de liaison pour commuter les paquets étiquetés.
3. **`siège` (Routeur Client) :** 
   * Activation du routage IP (`ip routing`).
   * Configuration de l'interface locale et de la route par défaut vers le PE (`sp1`).

---

## 🚀 Commandes de Validation Clés (pour Screen Record)

### 1. Sur le routeur PE (`sp1`) : Vérification de la VRF
```text
show ip vrf
show ip route vrf Client_A
