<section class="accessibilite-ls" style="max-width:900px;margin:auto;font-size:1.1rem;line-height:1.6;">

<header>
  <h1 style="text-align:center;font-size:2rem;margin-bottom:1rem;">
    ✨ Des questionnaires en ligne plus simples, plus clairs, plus accessibles
  </h1>
  <p style="text-align:center;color:#555;">
    <b>Université de Lille • Pack Accessibilité LimeSurvey compatible version 6.3.9+231211 / 6.15.22+251103</b>
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
    <li>✔️ Validation <strong>pas à pas</strong> : seule la première question en erreur est affichée.</li>
    <li>✔️ Message d’erreur affiché directement auprès de la question concernée.</li>
    <li>✔️ Focus automatique sur l’endroit à corriger.</li>
  </ul>
  <p>💡 Résultat : vous savez <strong>exactement quoi faire</strong> pour avancer, sans stress.</p>

  <hr>

  <!-- STRUCTURE -->
  <h2>🧩 Des questionnaires mieux organisés et plus compréhensibles</h2>
  <ul>
    <li>🗂️ Groupes de réponses mieux identifiés (Oui/Non, listes, cases à cocher…).</li>
    <li>👀 <strong>Utilisation correcte des landmarks HTML</strong> : 
      <code>&lt;header role="banner"&gt;</code>, <code>&lt;main role="main"&gt;</code>, 
      <code>&lt;footer role="contentinfo"&gt;</code>.
      <br><em>(LimeSurvey n’en utilise pas nativement, nous les avons ajoutés.)</em>
    </li>
    <li>🧱 Champs obligatoires seulement lorsqu’ils sont visibles.</li>
    <li>🚫 Plus de blocages causés par des champs cachés ou non pertinents.</li>
  </ul>

  <hr>

  <!-- DESIGN -->
  <h2>🎨 Un affichage plus confortable : contraste, couleurs et focus visibles</h2>
  <ul>
    <li>🎨 <strong>Correction des contrastes</strong> et couleurs trop faibles.</li>
    <li>🔍 <strong>Focus clavier renforcé</strong> sur les boutons radio 🔘 et cases à cocher ☑️ : contour net + fond clair.</li>
    <li>🖱️ Meilleure visibilité pour les utilisateurs au clavier ou malvoyants.</li>
  </ul>

  <hr>

  <!-- CHAMPS -->
  <h2>📅 Saisir une date, un email ou un numéro : enfin simple</h2>
  <ul>
    <li>📅 Dates en trois champs clairs : <strong>Jour / Mois / Année</strong>.</li>
    <li>✉️ Champs email optimisés pour smartphone (clavier email).</li>
    <li>📱 Téléphone et chiffres : saisie numérique adaptée.</li>
    <li>🗑️ Suppression des calendriers doublons de LimeSurvey.</li>
  </ul>

  <hr>

  <!-- AUTRE -->
  <h2>💬 “Autre, précisez” devient clair et logique</h2>
  <ul>
    <li>✨ Le champ texte “Autre” apparaît uniquement si l’option “Autre” est choisie.</li>
    <li>🔁 Taper du texte coche automatiquement “Autre”.</li>
    <li>😌 Plus de messages d’erreur sur des commentaires non concernés.</li>
  </ul>

  <hr>

  <!-- ARIA -->
  <h2>🗣️ Messages accessibles et retours vocaux</h2>
  <ul>
    <li>🔔 Alerte correctement annoncée par les lecteurs d’écran au bon moment.</li>
    <li>🤫 Les textes d’aide ne sont plus lus comme des “alertes”.</li>
    <li>⏳ Message vocal lors de l’envoi : “Votre formulaire est en cours de traitement.”</li>
    <li>🎉 <strong>Message final avec rôle d’alerte :</strong>  
      “Vos réponses ont bien été enregistrées.”</li>
  </ul>

  <hr>

  <!-- CLAVIER -->
  <h2>⌨️ Confort renforcé pour les utilisateurs au clavier</h2>
  <ul>
    <li>↩️ La touche <strong>Entrée</strong> permet d’avancer logiquement.</li>
    <li>🎯 Indicateur de focus visuel beaucoup plus net.</li>
    <li>♿ Navigation fluide sans souris.</li>
  </ul>

  <hr>

<section id="notice-grand-public-4f-4g" style="max-width:900px;margin:auto;line-height:1.6;font-size:1rem;">

  <h2>Questions “Si oui…” : un fonctionnement plus simple et plus logique</h2>

  <p>
    Dans beaucoup de questionnaires, certaines questions dépendent d’une réponse précédente.
    Par exemple :
  </p>
  <blockquote>
    <p><strong>Q1 :</strong> Êtes-vous fumeur ?</p>
    <p><strong>Q2 :</strong> Si oui, combien de cigarettes par jour ?</p>
  </blockquote>

  <p>
    Les scripts 4f et 4g améliorent ce comportement dans LimeSurvey pour que
    <strong>tout soit plus clair pour les répondants</strong> et plus fiable pour les équipes.
  </p>

  <hr>

  <h3>1. Réaffichage automatique des questions pertinentes</h3>

  <p>
    Parfois, LimeSurvey considère qu’une question devrait être à nouveau affichée,
    mais elle reste pourtant cachée à l’écran. Cela peut créer des blocages
    ou des incohérences.
  </p>

  <p>Le script :</p>
  <ul>
    <li>surveille les questions qui redeviennent “pertinentes” ;</li>
    <li>les réaffiche automatiquement si elles étaient encore masquées ;</li>
    <li>corrige les paramètres techniques (attributs HTML, accessibilité) pour que tout reste cohérent.</li>
  </ul>

  <p>
    Résultat : <strong>aucune question “fantôme”</strong> ne vient perturber la réponse au questionnaire.
  </p>

  <hr>

  <h3>2. Gestion automatique des questions “Si oui…”</h3>

  <p>
    Le script repère tout seul les questions qui commencent par <strong>“Si oui…”</strong> ou
    celles que l’on a marquées comme dépendantes. Elles deviennent alors des
    “questions enfants” de la question précédente.
  </p>

  <p>Ensuite :</p>
  <ul>
    <li>si la réponse “Oui” est cochée à la question précédente, la question “Si oui…” apparaît ;</li>
    <li>si ce n’est pas le cas, la question “Si oui…” est masquée et ses réponses sont vidées.</li>
  </ul>

  <p>
    Ainsi, le répondant ne voit <strong>que les questions qui le concernent vraiment</strong>, et les
    anciennes réponses ne créent pas de blocages.
  </p>

  <hr>

  <h3>3. Nettoyage des réponses sur les questions masquées</h3>

  <p>Lorsqu’une question dépendante est masquée, le script :</p>
  <ul>
    <li>décoche les cases et boutons radio ;</li>
    <li>réinitialise les listes déroulantes ;</li>
    <li>efface les textes saisis ;</li>
    <li>retire l’obligation de répondre (champ “obligatoire”).</li>
  </ul>

  <p>
    Résultat : <strong>le questionnaire ne peut plus se bloquer</strong> à cause d’une réponse cachée
    dans une question invisible.
  </p>

  <hr>

  <h3>4. Accessibilité renforcée</h3>

  <p>
    Pour les personnes utilisant un clavier ou un lecteur d’écran, il est important que
    les questions soient correctement signalées comme visibles ou cachées.
  </p>

  <p>Les scripts 4f et 4g veillent à :</p>
  <ul>
    <li>retirer les questions cachées du parcours de navigation (clavier, lecteur d’écran) ;</li>
    <li>marquer correctement les questions visibles comme telles ;</li>
    <li>éviter les champs “obligatoires” non visibles.</li>
  </ul>

  <p>
    Cela contribue à rendre les questionnaires plus <strong>accessibles</strong> et plus confortables
    pour toutes et tous.
  </p>

  <hr>

  <h3>5. Une expérience plus fluide pour les répondants</h3>

  <p>
    Avec ces améliorations, les questionnaires :
  </p>
  <ul>
    <li>s’adaptent automatiquement aux réponses de l’utilisateur ;</li>
    <li>affichent seulement les questions vraiment utiles ;</li>
    <li>limitent les risques d’erreurs ou de blocages au moment de l’envoi.</li>
  </ul>

  <p>
    En résumé, les scripts 4f et 4g permettent de proposer des
    <strong>parcours de questions conditionnelles</strong> plus clairs, plus stables et plus respectueux
    des bonnes pratiques d’accessibilité.
  </p>

</section>

<hr>

  <!-- FOOT -->
  <footer role="contentinfo">
    <h2>🤝 Une démarche d’accessibilité continue</h2>
    <p>
      Ce pack est développé par la <strong>Direction du numérique – Service DAWAM • Université de Lille</strong>, 
      dans une volonté de respecter les bonnes pratiques du <strong>RGAA 4</strong> et d'améliorer constamment l’expérience utilisateur.
    </p>
    <p>
      📬 Contact : <a href="mailto:raphael.lecerf@univ-lille.fr">raphael.lecerf@univ-lille.fr</a> / <a href="mailto:support-liemsurvey@univ-lille.fr">support-limesurvey@univ-lille.fr</a>
    </p>
  </footer>

</main>

</section>
