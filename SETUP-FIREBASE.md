# Activer les comptes (Google) + la synchronisation cloud

Par défaut, l'application fonctionne **100 % en local** : chaque profil enfant et
chaque bilan sont enregistrés dans le navigateur de l'appareil (rien n'est envoyé
sur Internet). C'est suffisant pour tester et pour un usage personnel sur un seul
appareil.

Pour permettre aux utilisateurs de **se connecter avec leur adresse Google** et de
**retrouver leur historique sur n'importe quel appareil**, branchez un projet
**Firebase** (gratuit). Voici la marche à suivre — ~10 minutes, aucune carte
bancaire requise.

## 1. Créer le projet Firebase
1. Allez sur https://console.firebase.google.com → **Ajouter un projet**.
2. Donnez un nom (ex. `carnet-eveil`), validez (vous pouvez désactiver Analytics).

## 2. Activer la connexion Google
1. Menu **Build → Authentication → Get started**.
2. Onglet **Sign-in method** → activez **Google** → Enregistrer.
3. Onglet **Settings → Authorized domains** : ajoutez le domaine où le site est
   publié, par ex. `unepas2.github.io` (et `localhost` pour vos tests).

## 3. Créer la base Firestore
1. Menu **Build → Firestore Database → Create database**.
2. Choisissez un emplacement (pour le RGPD, privilégiez l'Europe, ex.
   `europe-west`), démarrez en mode **production**.
3. Onglet **Rules** : collez ces règles (chaque utilisateur n'accède qu'à ses
   propres données) puis **Publish** :

   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /users/{uid} {
         allow read, write: if request.auth != null && request.auth.uid == uid;
       }
     }
   }
   ```

## 4. Récupérer la config web
1. **Project settings** (⚙️) → section **Your apps** → icône **Web** (`</>`).
2. Enregistrez l'app (un surnom suffit), Firebase affiche un objet
   `firebaseConfig`. Copiez-le.

## 5. Coller la config dans l'application
Ouvrez `index.html`, repérez tout en haut du `<script>` la ligne :

```js
const FIREBASE_CONFIG = null;
```

Remplacez-la par votre objet, par exemple :

```js
const FIREBASE_CONFIG = {
  apiKey: "AIza...",
  authDomain: "carnet-eveil.firebaseapp.com",
  projectId: "carnet-eveil",
  storageBucket: "carnet-eveil.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123...:web:abc..."
};
```

> Ces clés sont **publiques** et peuvent figurer dans le code : la sécurité est
> assurée par les **règles Firestore** ci-dessus, pas par le secret des clés.

Enregistrez, redéployez. Un bouton **« Se connecter avec Google »** apparaît en
haut à droite. À la connexion, l'historique local est **fusionné** puis
synchronisé : l'utilisateur le retrouve sur tous ses appareils.

## Bon à savoir
- Sans config, ou si Firebase est injoignable, l'app **bascule automatiquement en
  mode local** : elle ne casse jamais.
- La synchronisation cloud nécessite que la page soit servie en **https** (GitHub
  Pages convient) ; en ouvrant le fichier en `file://`, seul le mode local est actif.

## ⚖️ Données personnelles (RGPD)
Vous stockez des données de développement d'un enfant rattachées à un compte
nominatif : ce sont des **données personnelles sensibles concernant un mineur**.
Avant une mise en production publique, prévoyez : information claire et
**consentement** du parent, **minimisation** des données, hébergement de
préférence **dans l'UE** (emplacement Firestore européen), une **politique de
confidentialité**, et la possibilité de **supprimer son compte et ses données**
(la suppression de profil efface déjà l'historique local et cloud associé).
