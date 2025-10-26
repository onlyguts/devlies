# DevLies

Bienvenue dans DevLies, un jeu multijoueur de déduction sociale inspiré du Loup-Garou, repensé en version développeur. Ce monorepo contient le frontend mobile (React Native / Expo) et le backend serveur (Node.js / Express / Socket.IO)

---

## 🕹️ Présentation du jeu

Dans ce combat classique entre le bien et le mal, deux équipes s’affrontent :

- **Les Développeurs** : Fidèles, ils cherchent à expulser tous les Hackers infiltrés.
- **Les Hackers** : Agents secrets, ils cherchent à corrompre le projet et à prendre le contrôle.

Le jeu alterne entre phases de jour (votes et discussions) et phases de nuit (actions secrètes), avec différents rôles pour chaque joueur :

| Rôle       | Description                                                                       |
|------------|-----------------------------------------------------------------------------------|
| **Hacker** | Élimine un Développeur chaque nuit et tente de déjouer les votes de jour.        |
| **Dev Junior** | Développeur loyal sans pouvoirs particuliers, se base sur la logique et la persuasion. |
| **DevOps** | Peut auditer un joueur chaque nuit pour connaître son rôle (Dev ou Hacker).       |
| **ChatGPT**| Protège un joueur chaque nuit d’une élimination.                                 |

---

## 🚀 Structure du monorepo

devlies/

├── frontend/ # Application mobile React Native / Expo

└── backend/ # Serveur Node.js / Express / Socket.IO

---

## 📱 Tester l’application mobile

![eas-update](https://github.com/user-attachments/assets/64710f0c-b100-4de8-8384-6a01555d173c)


---

## 📦 Frontend

L’application mobile permet aux joueurs de se connecter, rejoindre des parties en temps réel, discuter, voter, et personnaliser leur avatar.

### Fonctionnalités principales

- Multijoueur en temps réel avec Socket.IO
- Authentification persistante avec Redux Persist
- Progression des joueurs (XP, niveau, statistiques)
- Boutique en jeu pour skins cosmétiques
- Système d’amis et profils personnalisables
- Interface pixel art rétro

### Installation

```bash
cd frontend
npm install
```

Créer un fichier .env dans le dossier frontend avec les variables :

```env
EXPO_PUBLIC_API_URL=URL_DE_VOTRE_BACKEND
EXPO_PUBLIC_API_URL2=URL_DE_VOTRE_SERVEUR_SOCKET_IO
```

## 🖥️ Backend

Le serveur backend gère la logique du jeu, la communication en temps réel, l’authentification, la gestion des profils et les statistiques.

### Fonctionnalités principales

- Authentification sécurisée (hashage des mots de passe)
- Gestion des profils et progression
- Boutique et gestion des skins
- Système d’amis (demandes, acceptation, suppression)
- Cycle complet du jeu (lobby, phases, votes)
- Chats multiples (général, Hacker, DevOps)
- Tests d’intégration avec Jest

### Installation

```bash
cd backend
npm install
```

### Configuration

Créer un fichier `.env` dans le dossier `backend` avec la variable suivante, en remplaçant par vos identifiants MongoDB :

```env
URL_DB=mongodb+srv://<user>:<password>@cluster.mongodb.net/<dbname>
```

### Lancement du serveur

Pour démarrer le serveur en mode développement (avec rechargement automatique) :

```bash
npm run dev
```

## 📡 Communication en temps réel (Socket.IO)

Le backend gère les événements suivants :

- Gestion des lobbys (join, leave)
- Envoi et réception de messages (chat général et privés)
- Votes de jour et de nuit
- Actions des rôles (audit DevOps, protection ChatGPT)
- Gestion des phases du jeu (jour, nuit, vote)

