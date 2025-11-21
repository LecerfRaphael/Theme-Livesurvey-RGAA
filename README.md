<section class="accessibilite-ls" style="max-width:900px;margin:auto;font-size:1.1rem;line-height:1.6;">

  <header>
    <h1 style="text-align:center;font-size:2rem;margin-bottom:1rem;">
      ✨ Des questionnaires en ligne plus simples, plus clairs, plus accessibles
    </h1>
    <p style="text-align:center;color:#555;">
      <b>Université de Lille • Pack Accessibilité LimeSurvey<br>
      Compatible 6.3.9+231211 / 6.15.22+251103 • Version mise à jour le 21/11/2025</b>
    </p>
  </header>

  <main role="main">

    <p>
      À l’Université de Lille, nous avons profondément amélioré l’expérience des questionnaires LimeSurvey pour les rendre 
      <strong>plus agréables, plus intuitifs et plus accessibles à tous</strong> 😄  
      Que vous utilisiez un ordinateur, un smartphone, un clavier ou un lecteur d’écran…  
      <strong>moins de contraintes, plus de clarté.</strong>
    </p>

    <hr>

    <!-- NAVIGATION -->
    <h2>🧭 Une navigation plus fluide : une seule question à corriger à la fois</h2>
    <ul>
      <li>✔️ <strong>Validation pas à pas</strong> : seule la première question en erreur est signalée.</li>
      <li>✔️ Message d’erreur affiché directement <strong>au niveau de la question concernée</strong>.</li>
      <li>✔️ <strong>Focus automatique</strong> sur l’endroit à corriger, avec défilement doux.</li>
      <li>✔️ Les tableaux de réponses (questions en lignes/colonnes) sont traités correctement : 
        au moins une réponse par ligne lorsque c’est obligatoire.</li>
      <li>✔️ Les questions de date obligatoires détectent précisément ce qui manque :
        “Veuillez renseigner <em>le jour</em> / <em>le mois</em> / <em>l’année</em> …”.</li>
    </ul>
    <p>💡 Résultat : vous savez <strong>exactement quoi faire</strong> pour avancer, sans stress.</p>

    <hr>

    <!-- STRUCTURE -->
    <h2>🧩 Des questionnaires mieux organisés et plus compréhensibles</h2>
    <ul>
      <li>🗂️ Groupes de réponses (Oui/Non, listes, cases à cocher, commentaires, etc.) 
        transformés en <strong>blocs structurés</strong> pour les technologies d’assistance.</li>
      <li>👀 <strong>Utilisation correcte des landmarks HTML</strong> : 
        <code>&lt;header role="banner"&gt;</code>, <code>&lt;main role="main"&gt;</code>, 
        <code>&lt;footer role="contentinfo"&gt;</code>.
        <br><em>(LimeSurvey ne les propose pas nativement, nous les avons ajoutés.)</em>
      </li>
      <li>🧱 Champs obligatoires seulement lorsqu’ils sont <strong>visibles et pertinents</strong>.</li>
      <li>🚫 Plus de blocages causés par des champs cachés, désactivés ou “Autre” non pertinents.</li>
    </ul>

    <hr>

    <!-- DESIGN -->
    <h2>🎨 Un affichage plus confortable : contraste, couleurs et focus visibles</h2>
    <ul>
      <li>🎨 <strong>Correction des contrastes</strong> et des couleurs trop faibles pour une meilleure lisibilité.</li>
      <li>🔍 <strong>Focus clavier renforcé</strong> sur les boutons radio 🔘 et cases à cocher ☑️ 
        (contour net + halo + fond clair).</li>
      <li>🖱️ Meilleure visibilité des éléments sélectionnés pour les utilisateurs au clavier ou malvoyants.</li>
    </ul>

    <hr>

    <!-- CHAMPS -->
    <h2>📅 Saisir une date, un email ou un numéro : enfin simple</h2>
    <ul>
      <li>📅 Dates en trois champs clairs : <strong>Jour / Mois / Année</strong>, avec messages d’erreur adaptés.</li>
      <li>📅 Un champ technique caché au format <code>aaaa-mm-jj</code> est géré automatiquement pour LimeSurvey.</li>
      <li>🗑️ Suppression des <strong>calendriers doublons</strong> et widgets graphiques redondants.</li>
      <li>✉️ Champs email optimisés pour smartphone (clavier “email”, suggestions adaptées).</li>
      <li>📱 Téléphone et valeurs numériques : saisie numérique et contraintes adaptées (step, inputmode…).</li>
    </ul>

    <hr>

    <!-- AUTRE -->
    <h2>💬 “Autre, précisez” devient clair et logique</h2>
    <ul>
      <li>✨ Le champ texte “Autre” apparaît uniquement si l’option “Autre” est cochée.</li>
      <li>🔁 Si vous commencez à taper dans “Autre, précisez…”, la case “Autre” se coche automatiquement.</li>
      <li>🧠 Les réponses “Autre” sont correctement prises en compte par LimeSurvey (y compris les champs techniques internes).</li>
      <li>😌 Plus de messages d’erreur sur des commentaires qui ne devraient pas être remplis.</li>
      <li>🎯 Sur certaines questions, l’option “Autre” peut être entièrement désactivée (quand elle n’a pas de sens).</li>
    </ul>

    <hr>

    <!-- LIST-WITH-COMMENT / COMMENTAIRES -->
    <h2>📝 Cases à cocher avec commentaires : plus cohérentes</h2>
    <ul>
      <li>📋 Pour les questions “cases à cocher + commentaire” :
        <ul>
          <li>Si aucune case n’est cochée 👉 les commentaires restent facultatifs.</li>
          <li>Si au moins une case est cochée 👉 le commentaire de cette ligne devient <strong>obligatoire</strong>.</li>
        </ul>
      </li>
      <li>🚫 Les commentaires sur des lignes non cochées sont automatiquement désactivés.</li>
      <li>🛡️ En cas d’erreur, un commentaire sur une ligne non cochée n’empêche plus l’envoi du formulaire.</li>
    </ul>

    <hr>

    <!-- QUESTIONS SI OUI -->
    <h2>😄 Questions “Si oui…” : un fonctionnement plus simple et plus logique</h2>

    <p>
      Dans beaucoup de questionnaires, certaines questions dépendent d’une réponse précédente.
      Par exemple :
    </p>
    <blockquote>
      <p><strong>Q1 :</strong> Êtes-vous fumeur ?</p>
      <p><strong>Q2 :</strong> Si oui, combien de cigarettes par jour ?</p>
    </blockquote>

    <p>
      Le pack détecte automatiquement les questions dont la légende commence par
      <strong>“Si oui…”</strong> et les relie à la question précédente.
    </p>

    <ul>
      <li>✅ Si la réponse “Oui” est cochée à la question précédente → la question “Si oui…” apparaît.</li>
      <li>🚫 Sinon, la question “Si oui…” est masquée, ses réponses sont vidées et ne sont plus obligatoires.</li>
      <li>♿ Les questions masquées sont correctement retirées de la navigation (clavier, lecteur d’écran).</li>
    </ul>

    <p>
      ✨ <strong>Résultat :</strong> la personne ne voit que les questions qui la concernent vraiment, sans blocage ni surprise.
    </p>

    <hr>

    <!-- ARIA / MESSAGES -->
    <h2>🗣️ Messages accessibles et retours vocaux</h2>
    <ul>
      <li>🔔 Les messages importants sont gérés via des zones <strong>aria-live</strong> adaptées.</li>
      <li>🤫 Les textes d’aide des questions ne sont plus lus comme des “alertes” en permanence.</li>
      <li>⏳ Lors de l’envoi, un message est annoncé : 
        <em>“Votre formulaire est en cours de traitement.”</em></li>
      <li>🎉 À la fin, un message clair confirme que vos réponses ont bien été enregistrées.</li>
      <li>🔳 La fenêtre modale d’alerte de LimeSurvey est enrichie pour être mieux annoncée aux lecteurs d’écran.</li>
    </ul>

    <hr>

    <!-- CLAVIER -->
    <h2>⌨️ Confort renforcé pour les utilisateurs au clavier</h2>
    <ul>
      <li>↩️ La touche <strong>Entrée</strong> permet d’avancer logiquement (Suivant / Envoyer) tout en respectant les champs texte.</li>
      <li>🎯 Indicateur de focus visuel beaucoup plus net sur les choix de réponse.</li>
      <li>♿ Navigation fluide sans souris, y compris dans les tableaux et les groupes complexes.</li>
    </ul>

    <hr>

    <!-- FOOT -->
    <footer role="contentinfo">
      <h2>🤝 Une démarche d’accessibilité continue</h2>
      <p>
        Ce pack est développé par la <strong>Direction du numérique – Service DAWAM • Université de Lille</strong>, 
        dans une volonté de respecter les bonnes pratiques du <strong>RGAA 4</strong> et d'améliorer constamment l’expérience utilisateur.
      </p>
      <p>
        📬 Contact : 
        <a href="mailto:raphael.lecerf@univ-lille.fr">raphael.lecerf@univ-lille.fr</a> • 
        <a href="mailto:support-limesurvey@univ-lille.fr">support-limesurvey@univ-lille.fr</a>
      </p>
    </footer>

  </main>

</section>
