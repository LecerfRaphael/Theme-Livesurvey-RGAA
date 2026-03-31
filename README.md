<p align="center">
  <strong>✨ Des questionnaires en ligne plus simples, plus clairs, plus accessibles</strong><br>
  Université de Lille • Pack Accessibilité LimeSurvey<br>
  Compatible 6.3.9+231211 / 6.15.22+251103 • Version mise à jour le 05/12/2025<br>
  - Licence : CC BY-NC-SA -
</p>

<p>L'accessibilité numérique est un enjeu majeur pour garantir l'inclusion de tous les utilisateurs, y compris les personnes en situation de handicap. En suivant le Référentiel Général d'Amélioration de l'Accessibilité (RGAA), l'Université de Lille a travaillé sur la refonte des templates utilisés par l'application LimeSurvey, pour que ces derniers  deviennent plus compréhensibles et utilisables par un public plus large. </p>

<p>Sur ce git, vous trouverez le zip de notre template (version stable) que vous pourrez installer (pré requis : thème Fruity de base) ainsi qu'une version Beta.</p>

<p>Ce travail est mis à disponibilité des membres de l'<b>APRANESR (association des référents accessibilité numérique de l’enseignant supérieur et de la recherche)</b></p>


<h2>🤝 Une démarche d’accessibilité continue</h2>
<p>
  Ce pack est développé par la <strong>Direction du numérique – Service DAWAM • Université de Lille</strong>,<br>
  dans une volonté de respecter les bonnes pratiques du <strong>RGAA 4</strong> et d'améliorer constamment l’expérience utilisateur.
</p>

<p>
  📬 Contact :<br>
  <a href="mailto:contact@apranesr.fr">contact APRANESR</a> •
  <a href="mailto:raphael.lecerf@univ-lille.fr">raphael.lecerf@univ-lille.fr</a> •
  <a href="mailto:support-limesurvey@univ-lille.fr">support-limesurvey@univ-lille.fr</a>
</p>
<hr>

<h2>🧭 Une navigation plus fluide : une seule question à corriger à la fois</h2>
<ul>
  <li>✔️ <strong>Validation pas à pas</strong> : seule la première question en erreur est signalée.</li>
  <li>✔️ Message d’erreur affiché directement <strong>au niveau de la question concernée</strong>.</li>
  <li>✔️ <strong>Focus automatique</strong> sur l’endroit à corriger (avec défilement doux).</li>
  <li>✔️ Les tableaux de réponses (questions en lignes/colonnes) sont traités correctement : au moins une réponse par ligne lorsque c’est obligatoire.</li>
  <li>✔️ Les questions de date obligatoires détectent précisément ce qui manque :
    <em>“Veuillez renseigner le jour / le mois / l’année…”</em>.
  </li>
  <li>🔔 Une <strong>alerte accessibilité</strong> en haut de page résume les problèmes restants et disparaît dès que tout est corrigé.</li>
</ul>
<p>💡 Résultat : vous savez <strong>exactement quoi faire</strong> pour avancer, sans stress.</p>

<hr>

<h2>🧩 Des questionnaires mieux organisés et plus compréhensibles</h2>
<ul>
  <li>🗂️ Groupes de réponses (Oui/Non, listes, cases à cocher, commentaires, etc.) transformés en <strong>blocs structurés</strong>.</li>
  <li>👀 <strong>Utilisation correcte des landmarks HTML</strong> :<br>
    <code>&lt;header role="banner"&gt;</code>, <code>&lt;main role="main"&gt;</code>, <code>&lt;footer role="contentinfo"&gt;</code><br>
    <em>(LimeSurvey ne les propose pas nativement, nous les avons ajoutés.)</em>
  </li>
  <li>🧱 Champs obligatoires seulement lorsqu’ils sont <strong>visibles et pertinents</strong>.</li>
  <li>🚫 Plus de blocages causés par des champs cachés, désactivés ou “Autre” non pertinents.</li>
</ul>

<hr>

<h2>🎨 Un affichage plus confortable : contraste, couleurs et focus visibles</h2>
<ul>
  <li>🎨 <strong>Correction des contrastes</strong> et des couleurs trop faibles.</li>
  <li>🔍 <strong>Focus clavier renforcé</strong> sur les boutons radio 🔘 et cases à cocher ☑️
    (contour net + halo + fond clair).</li>
  <li>🖱️ Meilleure visibilité pour les utilisateurs au clavier ou malvoyants.</li>
</ul>

<hr>

<h2>📅 Saisir une date, un email ou un numéro : enfin simple</h2>
<ul>
  <li>📅 Dates en trois champs clairs : <strong>Jour / Mois / Année</strong>.</li>
  <li>📅 Un champ technique caché au format <code>aaaa-mm-jj</code> est géré automatiquement pour LimeSurvey.</li>
  <li>🗑️ Suppression des <strong>calendriers doublons</strong> et widgets graphiques redondants.</li>
  <li>✉️ Champs email optimisés pour smartphone (clavier “email”).</li>
  <li>📱 Téléphone et valeurs numériques : saisie numérique adaptée (<code>step</code>, <code>inputmode</code>…).</li>
  <li>🚦 Sur les champs texte ou nombre, un <strong>contrôle de longueur</strong> prévient lorsqu’on atteint la taille maximale attendue (attribut <code>size</code> / <code>maxlength</code>), avant que cela ne devienne bloquant.</li>
</ul>

<hr>

<h2>💬 “Autre, précisez” devient clair et logique</h2>
<ul>
  <li>✨ Le champ texte “Autre” apparaît uniquement si l’option “Autre” est cochée.</li>
  <li>🔁 Si vous commencez à taper dans “Autre, précisez…”, la case “Autre” se coche automatiquement.</li>
  <li>🧠 Les réponses “Autre” sont correctement prises en compte par LimeSurvey, y compris les champs techniques internes.</li>
  <li>😌 Plus de messages d’erreur sur des commentaires qui ne devraient pas être remplis.</li>
  <li>🎯 Sur certaines questions, l’option “Autre” peut être entièrement désactivée (quand elle n’a pas de sens).</li>
</ul>

<hr>

<h2>📝 Cases à cocher avec commentaires : plus cohérentes</h2>
<ul>
  <li>📋 Pour les questions “cases à cocher + commentaire” :
    <ul>
      <li>Si <strong>aucune case</strong> n’est cochée → les commentaires restent facultatifs.</li>
      <li>Si <strong>au moins une case</strong> est cochée → le commentaire de cette ligne devient <strong>obligatoire</strong>.</li>
    </ul>
  </li>
  <li>🚫 Les commentaires sur des lignes non cochées sont automatiquement désactivés.</li>
  <li>🛡️ En cas d’erreur, un commentaire sur une ligne non cochée n’empêche plus l’envoi du formulaire.</li>
</ul>

<hr>

<h2>🗣️ Messages accessibles et retours vocaux</h2>
<ul>
  <li>🔔 Les messages importants sont gérés via des zones <strong><code>aria-live</code></strong> adaptées.</li>
  <li>🤫 Les textes d’aide ne sont plus lus comme des “alertes” en permanence.</li>
  <li>⏳ Lors de l’envoi, un message est annoncé :
    <em>“Votre formulaire est en cours de traitement.”</em>
  </li>
  <li>🎉 À la fin, un message clair confirme que vos réponses ont bien été enregistrées.</li>
  <li>🔳 La fenêtre modale d’alerte de LimeSurvey est enrichie pour être mieux annoncée aux lecteurs d’écran.</li>
  <li>📢 L’alerte accessibilité s’actualise dynamiquement : elle apparaît lorsqu’un problème est détecté, puis se ferme automatiquement dès que tout est conforme.</li>
</ul>

<hr>

<h2>⌨️ Confort renforcé pour les utilisateurs au clavier</h2>
<ul>
  <li>↩️ La touche <strong>Entrée</strong> permet d’avancer logiquement (Suivant / Envoyer) tout en respectant les champs texte.</li>
  <li>🎯 Indicateur de focus visuel beaucoup plus net sur les choix de réponse.</li>
  <li>♿ Navigation fluide sans souris, y compris dans les tableaux et les groupes complexes.</li>
</ul>

