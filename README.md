# 🌤️ MeteoAI — Hondeghem

**La météo qui apprend de ses erreurs.**

Application météo web pour Hondeghem (Nord, Hauts-de-France) : fusion pondérée de 7 modèles officiels (AROME, ARPEGE, ICON, ECMWF, GFS, GEM, UKMET), Weather Stability Index™, et historique prévu/réel conservé sur l'appareil.

## ✨ Fonctionnalités

- 🌡️ Dashboard temps réel (Open-Meteo — gratuit, sans clé API)
- 🕐 Prévisions heure par heure (30 h) et tendance 10 jours
- 🛡️ Weather Stability Index™ (variabilité thermique, bascule pluie, changements de régime)
- 📚 Historique persistant (localStorage) : compare la prévision J+1 de la veille au réel du jour, calcule MAE et biais
- 📈 Fiabilité comparée des 7 modèles + classement des stations d'observation du Nord
- 🧪 AI Lab : détection des régimes météorologiques actifs
- 🎨 Design glassmorphism : dégradé bleu ciel → indigo, cartes en verre dépoli
- 📴 Fonctionne hors-ligne une fois installée (service worker)

## 🚀 Utilisation

### En local

Télécharger le dépôt puis ouvrir `index.html` dans un navigateur. Les données en direct et l'historique fonctionnent ; seule l'installation PWA nécessite HTTPS.

### En ligne — GitHub Pages

1. Sur GitHub : **Settings → Pages**
2. Source : **Deploy from a branch** → branche `main`, dossier `/ (root)`
3. L'application sera disponible sur : `https://nicolas597474-eng.github.io/Meteo-Hondeghem/`

### 📱 Installer sur le téléphone

- **Android (Chrome)** : ouvrir l'adresse → menu ⋮ → « Ajouter à l'écran d'accueil »
- **iOS (Safari)** : bouton Partager → « Sur l'écran d'accueil »

## 🔧 Technique

- HTML / CSS / JavaScript autonomes — aucune dépendance, aucun build
- API : [Open-Meteo](https://open-meteo.com) (position Hondeghem : 50.757, 2.521)
- Historique : `localStorage` (clé `meteoai-history`)
- PWA : `manifest.webmanifest` + service worker (`sw.js`) pour le hors-ligne

## 🧠 Algorithme MeteoAI (démonstration)

Chaque modèle officiel dévie de la référence selon son profil d'erreur historique (MAE, RMSE, biais). Les poids de fusion, proportionnels à `1/(RMSE+0,3)`, sont recalculés à chaque ouverture : la prévision s'adapte dynamiquement.

---

D'après l'architecture de [meteo-ai-app](https://github.com/nicolas597474-eng/meteo-ai-app).