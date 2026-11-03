# SecMet — versions publiées

Livrables de chaque version de **SecMet** (effacement sécurisé et certifié de disques sous Linux, NIST SP 800-88) : paquets `.deb` et `.rpm`, AppImage, `SHA256SUMS` signé et `latest.json`.

## Installer (testeurs)

Une seule installation à la main ; ensuite, SecMet se met à jour depuis ses Réglages.

**Ubuntu 24.04, Linux Mint 22, Debian 13** (glibc ≥ 2.39) :

```bash
wget https://github.com/hclcdev12/secmet-releases/releases/latest/download/secmet_0.3.3-ubuntu24.04_amd64.deb
sudo apt install ./secmet_0.3.3-ubuntu24.04_amd64.deb
```

**Ubuntu 22.04, Linux Mint 21, Debian 12** :

```bash
wget https://github.com/hclcdev12/secmet-releases/releases/latest/download/secmet_0.3.3-ubuntu22.04_amd64.deb
sudo apt install ./secmet_0.3.3-ubuntu22.04_amd64.deb
```

**Fedora 42** : `sudo dnf install ./secmet-0.3.3-1.fc42.x86_64.rpm`.

**Autre distribution** : l'AppImage (`chmod +x`, puis lancer ; au premier lancement, un mot de passe administrateur installe le composant système).

Lancer **SecMet** depuis le menu des applications. Le mot de passe demandé au démarrage est celui de votre compte administrateur : il protège les opérations sur les disques.

## Mettre à jour

SecMet vérifie une fois par jour s'il existe une version plus récente (une requête HTTPS, sans donnée personnelle). Un point jaune apparaît alors sur le bouton Réglages. Dans **Réglages → Mises à jour**, cliquer **Installer la mise à jour** : le paquet est téléchargé, son empreinte vérifiée contre `SHA256SUMS` signé, puis installé (mot de passe administrateur). **Relancer SecMet** démarre la nouvelle version.

## Vérifier une version à la main

Chaque release contient `SHA256SUMS`, `SHA256SUMS.sig` et `latest.json`, signés par la clé de version de SecMet :

- identifiant `7854d9fe5a5e2be6`
- clé publique Ed25519 `bde3e3d9de271f8de9bb26c8dd4ed73f4c7344e309ebac7c3dffd50e02ca3bd5`

```bash
sha256sum -c SHA256SUMS            # empreintes des fichiers
```

La signature de `SHA256SUMS` et de `latest.json` se vérifie avec l'outil `secmet-release` des sources de SecMet (`secmet-release verify <dossier> --trust <clé publique>`). L'application le fait elle-même avant toute mise à jour.

## Retours de test

Décrire ce qui a été fait, ce qui était attendu, ce qui s'est passé, avec la version (Réglages → Mises à jour) et, si possible, le journal de session (`~/.secmet_logs/`). Les disques effacés le sont définitivement : ne tester qu'avec des disques dédiés.

Dernière version : `https://github.com/hclcdev12/secmet-releases/releases/latest/download/latest.json`
