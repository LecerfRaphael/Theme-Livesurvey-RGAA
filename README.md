<p align="center">
  <strong>✨ Des questionnaires en ligne plus simples, plus clairs, plus accessibles</strong><br>
  Université de Lille • Pack Accessibilité LimeSurvey<br>
  Compatible 6.3.9+231211 / 6.15.22+251103 • Version mise à jour le 21/11/2025
</p>

---

## 🧭 Une navigation plus fluide : une seule question à corriger à la fois

- ✔️ **Validation pas à pas** : seule la première question en erreur est signalée.
- ✔️ Message d’erreur affiché directement **au niveau de la question concernée**.
- ✔️ **Focus automatique** sur l’endroit à corriger (avec défilement doux).
- ✔️ Les tableaux de réponses (questions en lignes/colonnes) sont traités correctement :  
  au moins une réponse par ligne lorsque c’est obligatoire.
- ✔️ Les questions de date obligatoires détectent précisément ce qui manque :  
  “Veuillez renseigner _le jour_ / _le mois_ / _l’année_ …”.

💡 Résultat : vous savez **exactement quoi faire** pour avancer, sans stress.

---

## 🧩 Des questionnaires mieux organisés et plus compréhensibles

- 🗂️ Groupes de réponses (Oui/Non, listes, cases à cocher, commentaires, etc.) transformés en **blocs structurés**.
- 👀 **Utilisation correcte des landmarks HTML** :  
  `<header role="banner">`, `<main role="main">`, `<footer role="contentinfo">`  
  _(LimeSurvey ne les propose pas nativement, nous les avons ajoutés.)_
- 🧱 Champs obligatoires seulement lorsqu’ils sont **visibles et pertinents**.
- 🚫 Plus de blocages causés par des champs cachés, désactivés ou “Autre” non pertinents.

---

## 🎨 Un affichage plus confortable : contraste, couleurs et focus visibles

- 🎨 **Correction des contrastes** et des couleurs trop faibles.
- 🔍 **Focus clavier renforcé** sur les boutons radio 🔘 et cases à cocher ☑️  
  (contour net + halo + fond clair).
- 🖱️ Meilleure visibilité pour les utilisateurs au clavier ou malvoyants.

---

## 📅 Saisir une date, un email ou un numéro : enfin simple

- 📅 Dates en trois champs clairs : **Jour / Mois / Année**.
- 📅 Un champ technique caché au format `aaaa-mm-jj` est géré automatiquement pour LimeSurvey.
- 🗑️ Suppression des **calendriers doublons** et widgets graphiques redondants.
- ✉️ Champs email optimisés pour smartphone (clavier “email”).
- 📱 Téléphone et valeurs numériques : saisie numérique adaptée (step, inputmode…).

---

## 💬 “Autre, précisez” devient clair et logique

- ✨ Le champ texte “Autre” apparaît uniquement si l’option “Autre” est cochée.
- 🔁 Si vous commencez à taper dans “Autre, précisez…”, la case “Autre” se coche automatiquement.
- 🧠 Les réponses “Autre” sont correctement prises en compte par LimeSurvey, y compris les champs techniques internes.
- 😌 Plus de messages d’erreur sur des commentaires qui ne devraient pas être remplis.
- 🎯 Sur certaines questions, l’option “Autre” peut être entièrement désactivée (quand elle n’a pas de sens).

---

## 📝 Cases à cocher avec commentaires : plus cohérentes

- 📋 Pour les questions “cases à cocher + commentaire” :
  - Si **aucune case** n’est cochée → les commentaires restent facultatifs.
  - Si **au moins une case** est cochée → le commentaire de cette ligne devient **obligatoire**.
- 🚫 Les commentaires sur des lignes non cochées sont automatiquement désactivés.
- 🛡️ En cas d’erreur, un commentaire sur une ligne non cochée n’empêche plus l’envoi du formulaire.

---

## 😄 Questions “Si oui…” : un fonctionnement plus simple et plus logique

Dans beaucoup de questionnaires, certaines questions dépendent d’une réponse précédente.  
Par exemple :

> **Q1 :** Êtes-vous fumeur ?  
> **Q2 :** Si oui, combien de cigarettes par jour ?

Le pack détecte automatiquement les questions dont la légende commence par **“Si oui…”** et les relie à la question précédente :

- ✅ Si la réponse “Oui” est cochée à la question précédente → la question “Si oui…” apparaît.
- 🚫 Sinon, la question “Si oui…” est masquée, ses réponses sont vidées et ne sont plus obligatoires.
- ♿ Les questions masquées sont correctement retirées de la navigation (clavier, lecteur d’écran).

✨ Résultat : la personne ne voit **que les questions qui la concernent vraiment**, sans blocage ni surprise.

---

## 🗣️ Messages accessibles et retours vocaux

- 🔔 Les messages importants sont gérés via des zones **aria-live** adaptées.
- 🤫 Les textes d’aide ne sont plus lus comme des “alertes” en permanence.
- ⏳ Lors de l’envoi, un message est annoncé :  
  _“Votre formulaire est en cours de traitement.”_
- 🎉 À la fin, un message clair confirme que vos réponses ont bien été enregistrées.
- 🔳 La fenêtre modale d’alerte de LimeSurvey est enrichie pour être mieux annoncée aux lecteurs d’écran.

---

## ⌨️ Confort renforcé pour les utilisateurs au clavier

- ↩️ La touche **Entrée** permet d’avancer logiquement (Suivant / Envoyer) tout en respectant les champs texte.
- 🎯 Indicateur de focus visuel beaucoup plus net sur les choix de réponse.
- ♿ Navigation fluide sans souris, y compris dans les tableaux et les groupes complexes.

---

## 🤝 Une démarche d’accessibilité continue

Ce pack est développé par la **Direction du numérique – Service DAWAM • Université de Lille**,  
dans une volonté de respecter les bonnes pratiques du **RGAA 4** et d'améliorer constamment l’expérience utilisateur.

📬 Contact :  
[raphael.lecerf@univ-lille.fr](mailto:raphael.lecerf@univ-lille.fr) • [support-limesurvey@univ-lille.fr](mailto:support-limesurvey@univ-lille.fr)
