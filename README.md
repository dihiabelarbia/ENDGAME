# ENDGAME
PA 2024/2025 ESGI

 Mode opératoire – CV Parser
Authentification avec Firebase

Ce projet utilise Firebase Authentication (via Google Login) pour authentifier les utilisateurs.
🎯 Étapes pour configurer l’authentification :

    Créer un projet Firebase
    👉 Aller sur https://console.firebase.google.com, créer un nouveau projet (ou utiliser un existant).

    Activer l’authentification Google

        Dans le menu Firebase Console → Authentication

        Aller dans l’onglet "Méthode de connexion"

        Cliquer sur Google et l’activer

        Ajouter un domaine autorisé si besoin (ex. localhost, 127.0.0.1…)

    Obtenir la configuration Firebase Web

        Dans Project Settings (paramètres du projet) → onglet "Général"

        Dans "Vos applications", créer une app Web si ce n’est pas encore fait

        Copier le bloc de config comme ceci :

const firebaseConfig = {
  apiKey: "AIza...xyz",
  authDomain: "votre-projet.firebaseapp.com",
  projectId: "votre-projet",
  storageBucket: "votre-projet.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcxyz"
};

    Intégrer cette config dans le projet

        Dans le fichier src/firebase.js, ajoutez cette config :

import { initializeApp } from "firebase/app";

const firebaseConfig = {
  apiKey: "VOTRE_API_KEY",
  authDomain: "VOTRE_AUTH_DOMAIN",
  projectId: "VOTRE_PROJECT_ID",
  storageBucket: "VOTRE_BUCKET",
  messagingSenderId: "VOTRE_MSG_ID",
  appId: "VOTRE_APP_ID"
};

export const app = initializeApp(firebaseConfig);

    (Optionnel) Ajouter le signInWithPopup dans App.js pour connecter l’utilisateur :

import { getAuth, signInWithPopup, GoogleAuthProvider } from 'firebase/auth';

const auth = getAuth();
const provider = new GoogleAuthProvider();

signInWithPopup(auth, provider)
  .then((result) => {
    console.log("Utilisateur connecté :", result.user);
  })
  .catch((error) => {
    console.error("Erreur d'auth :", error);
  });

🚀 Lancer le projet localement
📦 Prérequis :

    Node.js v18+ installé

    Backend Flask lancé sur localhost:5000 (voir README backend)

🧱 Installation frontend

git clone https://github.com/dihiabelarbia/ENDGAME.git
cd ton-repo
npm install

▶️ Lancer l’application React

npm start

Cela ouvre automatiquement l'application sur http://localhost:3000.
📄 Résumé rapide
Action	Commande / Lien
Cloner le repo	git clone ...
Installer les dépendances	npm install
Lancer React	npm start
Lancer Flask (backend)	python app.py
Configurer Firebase Auth	console.firebase.google.com
