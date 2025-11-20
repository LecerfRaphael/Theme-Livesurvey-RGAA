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

<section id="notice-technique-4f-4g" style="max-width:900px;margin:auto;line-height:1.6;font-size:1rem;">

  <h2>Notice technique – Modules 4f et 4g (LimeSurvey)</h2>

  <p>
    Ces deux scripts JavaScript complètent le pack d’accessibilité LimeSurvey en apportant une
    gestion robuste de la <strong>visibilité des questions conditionnelles</strong> :
    synchronisation avec l’Expression Manager, masquage manuel maîtrisé, nettoyage des réponses
    et logique générique pour les questions de type <em>“Si oui…”</em>.
  </p>

  <h3>Objectifs principaux</h3>
  <ul>
    <li>Assurer la cohérence entre la <strong>pertinence EM</strong> (relevance) et l’<strong>affichage réel</strong> dans le DOM.</li>
    <li>Corriger automatiquement les questions qui redeviennent pertinentes mais restent masquées.</li>
    <li>Gérer de façon générique les questions dépendantes de type <strong>“Si oui, …”</strong> sans Expression Manager.</li>
    <li>Éviter tout blocage lié à des réponses résiduelles sur des questions masquées.</li>
    <li>Respecter les règles d’accessibilité (aria-hidden, focus, required, etc.).</li>
  </ul>

  <hr>

  <h3>4f – Réaffichage automatique des questions redevenues pertinentes</h3>

  <h4>Problème adressé</h4>
  <p>
    LimeSurvey laisse parfois des questions en état masqué (<code>ls-hidden</code>, <code>hidden</code>,
    <code>display:none</code>) alors que l’Expression Manager les considère de nouveau pertinentes
    (relevance = 1). Cela peut provoquer :
  </p>
  <ul>
    <li>des questions “fantômes” attendues mais invisibles ;</li>
    <li>des erreurs sur des champs <code>required</code> non visibles ;</li>
    <li>des incohérences de navigation au clavier et pour les lecteurs d’écran.</li>
  </ul>

  <h4>Principe de fonctionnement</h4>
  <ul>
    <li>Au chargement (<code>DOMContentLoaded</code>), le script parcourt toutes les questions :
      <code>fieldset[id^="question"]</code> et <code>div[id^="question"]</code>.
    </li>
    <li>Pour chaque question :
      <ul>
        <li>si l’ID commence par <code>question</code>,</li>
        <li>si la question n’est plus <code>ls-irrelevant</code>,</li>
        <li>si elle est encore masquée (<code>ls-hidden</code>, <code>hidden</code> ou <code>display:none</code>),</li>
        <li>et si elle n’a pas été masquée volontairement par JS (<code>data-ls-manual-hide="1"</code>),</li>
      </ul>
      alors la fonction <code>unhideIfRelevant()</code> la réaffiche.
    </li>
    <li>Un <code>MutationObserver</code> surveille ensuite les changements de classe :
      dès qu’une question voit son <code>ls-irrelevant</code> enlevé par LimeSurvey,
      <code>unhideIfRelevant()</code> est relancé.
    </li>
  </ul>

  <h4>Normalisation accessibilité appliquée</h4>
  <p>Lorsque la question est réaffichée, le script :</p>
  <ul>
    <li>retire <code>ls-hidden</code> ;</li>
    <li>retire l’attribut <code>hidden</code> ;</li>
    <li>réinitialise <code>style.display</code> si nécessaire ;</li>
    <li>positionne <code>aria-hidden="false"</code>.</li>
  </ul>

  <h4>Respect du masquage manuel</h4>
  <p>
    Si une question est masquée volontairement par le module 4g, elle porte
    <code>data-ls-manual-hide="1"</code>. Dans ce cas, <code>unhideIfRelevant()</code> ne la réouvrira
    pas, même si l’Expression Manager la juge pertinente.
  </p>

  <hr>

  <h3>4g – Gestion générique des questions “Si oui, …”</h3>

  <h4>Objectif</h4>
  <p>
    Proposer un mécanisme générique pour gérer les questions dépendantes,
    typiquement : « Si oui, précisez : … », sans avoir à écrire des conditions
    Expression Manager pour chaque cas.
  </p>

  <h4>Détection des questions enfants</h4>
  <p>Une question enfant est détectée si :</p>
  <ul>
    <li>le texte de son <code>&lt;legend&gt;</code> commence par <strong>“Si oui”</strong> (en minuscules après trim), ou</li>
    <li>la question possède la classe CSS <code>si-oui-child</code>.</li>
  </ul>

  <p>
    La fonction <code>initSiOuiQuestions()</code> parcourt tous les
    <code>fieldset.question-container</code> du DOM et identifie automatiquement ces questions enfants.
  </p>

  <h4>Détermination de la question parente</h4>
  <ul>
    <li>La question parente est recherchée via <code>previousElementSibling</code> en remontant
      jusqu’au précédent <code>fieldset.question-container</code> ou <code>div.question-container</code>.
    </li>
    <li>Si aucune question parente n’est trouvée, le couple parent/enfant est ignoré.</li>
  </ul>

  <h4>Logique d’affichage / masquage</h4>
  <p>La fonction <code>wireParentChildSiOui(parentQ, childQ)</code> :</p>
  <ul>
    <li>récupère tous les boutons radio de la question parente ;</li>
    <li>analyse le libellé des options pour trouver une option contenant “oui” ;</li>
    <li>si une option “Oui” est cochée → <strong>affiche</strong> la question enfant ;</li>
    <li>sinon → <strong>masque</strong> la question enfant et nettoie ses réponses.</li>
  </ul>

  <h4>Masquage manuel contrôlé</h4>
  <p>Lorsqu’une question enfant est masquée par 4g :</p>
  <ul>
    <li>elle reçoit <code>data-ls-manual-hide="1"</code> ;</li>
    <li>la classe <code>ls-hidden</code> est ajoutée ;</li>
    <li>les attributs <code>hidden="hidden"</code> et <code>aria-hidden="true"</code> sont posés ;</li>
    <li><code>style.display = "none"</code> est appliqué.</li>
  </ul>

  <p>
    Ce marquage garantit que 4f ne la réaffichera pas tant que l’utilisateur n’a pas mis “Oui” sur la
    question parente.
  </p>

  <h4>Nettoyage des réponses</h4>
  <p>Lors du masquage, 4g nettoie systématiquement les réponses de la question enfant :</p>
  <ul>
    <li>radios et checkboxes : <code>checked = false</code> ;</li>
    <li>listes déroulantes : <code>selectedIndex = 0</code> ;</li>
    <li>champs texte / textarea : <code>value = ""</code> ;</li>
    <li>attribut <code>required</code> retiré de tous les champs.</li>
  </ul>

  <p>
    Cela évite les validations bloquantes sur des réponses non visibles et maintient la
    cohérence des données côté serveur.
  </p>

  <h4>Accessibilité</h4>
  <ul>
    <li>Le masquage utilise <code>aria-hidden="true"</code> + <code>hidden</code> + <code>display:none</code> pour
      sortir la question du flux accessible.</li>
    <li>L’affichage remet <code>aria-hidden="false"</code> et retire les attributs de masquage.</li>
    <li>Aucune question masquée n’est laissée avec des champs <code>required</code>.</li>
  </ul>

  <hr>

  <h3>Intégration</h3>
  <ul>
    <li>Les scripts 4f et 4g peuvent être intégrés dans le fichier de thème (ex. <code>template.js</code>) de LimeSurvey.</li>
    <li>Ils reposent sur les classes standard LimeSurvey (<code>question-container</code>, <code>ls-hidden</code>,
      <code>ls-irrelevant</code>, etc.).</li>
    <li>Ils sont compatibles avec la navigation PJAX (<code>pjax:success</code>).</li>
  </ul>

  <p>
    Ensemble, ces modules renforcent la cohérence, la stabilité et l’accessibilité des questionnaires,
    en particulier pour les questions conditionnelles et les parcours complexes.
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
