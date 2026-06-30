# WebhookForge

**Orchestrez des workflows IA locaux depuis votre Mac — et depuis votre iPhone.**

WebhookForge est une application macOS native (SwiftUI + AppKit) qui pilote automatiquement Claude Code à votre place : elle reçoit un déclencheur, lance une session IA complète dans votre environnement local, et vous livre un résultat — site web généré, rapport produit, fichiers classés, scripts exécutés.

---

## Téléchargement

**[→ Télécharger la dernière version](https://github.com/WEB-DESIGN-PROD/webhookforge-releases/releases/latest)**

### Installation

1. Télécharger `WebhookForge.zip` depuis la dernière [release](https://github.com/WEB-DESIGN-PROD/webhookforge-releases/releases/latest)
2. Décompresser et déplacer `WebhookForge.app` dans `~/Applications/`
3. Premier lancement : **clic droit → Ouvrir** (contournement Gatekeeper, une seule fois)

### Prérequis

- macOS 14 Sonoma ou supérieur
- Claude Code installé et authentifié (`claude` dans le PATH)
- GitHub CLI installé et authentifié (`gh auth login`) — nécessaire uniquement pour les workflows avec création de repo

---

## Fonctionnalités

### Webhooks — Automation depuis le web

Recevez des données depuis n'importe quel service externe (formulaires, Zapier, Make, scripts, Raycast…) et déclenchez automatiquement une session Claude Code.

- Endpoint unique par webhook, sécurisé par signature HMAC-SHA256
- Création automatique d'un repo GitHub privé par client
- Copie d'un template de projet (Next.js, statique, etc.) avec `npm install` asynchrone
- Claude Code génère le site ou le livrable dans le repo local
- Preview instantanée sur `localhost` (serveur HTTP python ou `npm run dev`)
- Modification ultérieure via prompt texte, glisser-déposer d'image ou dictée vocale
- Support multi-fichiers : plusieurs images/documents transmis ensemble = une seule session Claude

**Exemple :** un formulaire de devis sur votre site envoie les données client → WebhookForge crée un repo privé, copie le template choisi, laisse l'IA personnaliser tout le site, et vous livre une URL de preview en quelques minutes.

---

### Tâches planifiées — Automation récurrente

Planifiez des sessions Claude Code selon votre propre calendrier, sans serveur externe.

| Type | Description |
|------|-------------|
| **Une fois** | Date et heure précises |
| **Jours de la semaine** | Ex. : lundi + mercredi à 09h00 |
| **Mensuel** | Le 1ᵉʳ du mois à 08h00 |
| **Intervalle** | Toutes les N minutes/heures |

- Dossier de travail configurable via sélecteur de dossier
- Pièces jointes optionnelles transmises à Claude
- Récupération automatique des tâches manquées (redémarrage après shutdown)
- Historique complet des exécutions avec logs en temps réel
- Notifications push : ✅ terminé / ❌ erreur / ⏰ manqué
- Hérite automatiquement de tous les MCPs configurés dans `~/.claude/`

**Exemples :**
- *Veille emails urgences* — tous les lundis 09h00, Claude lit Gmail via MCP et produit un rapport `.md` priorisé
- *Rapport analytics mensuel* — le 1ᵉʳ du mois, Claude interroge Amplitude et génère une synthèse
- *Backup configs* — tous les dimanches 23h, Claude archive vos dotfiles sur GitHub
- *Nettoyage Téléchargements* — chaque vendredi 18h, Claude trie et classe les fichiers par type

---

### Surveillance de dossiers — Automation déclenchée par vos fichiers

Surveillez un dossier : dès qu'un fichier y apparaît ou est modifié, Claude Code se déclenche automatiquement.

- Déclencheurs configurables indépendamment : ajout / modification / renommage / suppression
- Chemins exclus configurables (`.DS_Store`, caches, etc.)
- Icône orange distinctive + badge Claude sur chaque dossier surveillé dans le Finder
- Quick Actions dans le menu contextuel Finder (clic droit) pour déposer des fichiers ou activer la surveillance
- Raccourci global personnalisable (`⌃⌥⌘A`) pour ouvrir le panneau d'import rapide
- Détection automatique si le dossier est supprimé (badge orange d'alerte)
- Logs en temps réel et historique complet des runs

---

### App iPhone companion

Envoyez des fichiers, photos et documents depuis votre iPhone directement vers vos workflows Mac.

**Appairage QR code** — scannez le QR depuis les Réglages macOS, c'est fait.

**Deux destinations au choix à chaque envoi :**

- **→ Webhook** : le fichier est transmis à Claude Code via le webhook de votre choix
- **→ Dossier surveillé** : le fichier est copié directement dans le dossier, la surveillance se déclenche automatiquement

**Fonctionnalités :**
- Envoi de photos, vidéos et documents (sélection multiple)
- Dictée vocale → transcription → envoi au webhook
- Message/prompt optionnel joint à chaque envoi
- Groupement automatique : plusieurs fichiers = une seule session Claude
- Notifications push avec la vraie réponse de Claude
- Visibilité par webhook/dossier configurable depuis le Mac (toggle ON/OFF)
- Connexion WebSocket sécurisée, reconnexion automatique

---

## Mises à jour automatiques

WebhookForge vérifie les mises à jour au démarrage et affiche une bannière dans le tableau de bord si une nouvelle version est disponible. L'installation se fait en un clic, sans intervention manuelle.

---

## Confidentialité & Données

Toutes les sessions IA sont exécutées **localement** sur votre Mac, avec votre propre installation et votre propre authentification auprès du fournisseur IA de votre choix. WebhookForge n'a pas accès à vos données ni à vos échanges avec l'IA.

Consultez la [licence](./LICENSE) pour les conditions d'utilisation complètes.

---

## Licence

Ce logiciel est distribué sous licence propriétaire. Voir [LICENSE](./LICENSE).

© 2025–2026 WEB-DESIGN-PROD. Tous droits réservés.
