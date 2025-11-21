<section id="ameliorations-accessibilite" style="max-width:900px;margin:auto;line-height:1.6;font-size:1.05rem;">

  <h2>1. Détail des améliorations pour l’accessibilité (mise à jour le 21-11-2025)</h2>
  <p>Les optimisations ci-dessous sont regroupées par grandes thématiques RGAA / UX.</p>

  <!-- A) STRUCTURE -->
  <h3>A. Structure sémantique et navigation lecteur d’écran</h3>

  <h4>1) Transformation des &lt;div&gt; en &lt;fieldset&gt; + &lt;legend&gt;</h4>
  <p><strong>Script concerné :</strong> bloc “TRANSFORMATION DES DIV EN FIELDSET (list-dropdown, yes-no, numeric-multi, multiple-opt, list-radio, multiple-short-txt)”</p>

  <ul>
    <li>Les éléments :
      <code>div.list-dropdown</code>,
      <code>div.yes-no</code>,
      <code>div.numeric-multi</code>,
      <code>div.list-radio</code>,
      <code>div.multiple-opt</code>,
      <code>div.question-container.multiple-short-txt</code>  
      → sont remplacés dynamiquement par des <code>&lt;fieldset&gt;</code>.
    </li>
    <li>Le label de la question (<code>label.ls-label-question</code> ou <code>:scope &gt; label</code>) devient un <code>&lt;legend&gt;</code>.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Structure claire pour les lecteurs d’écran : chaque question est un groupe cohérent.</li>
    <li>Navigation plus logique (“form mode”) pour NVDA, JAWS et VoiceOver.</li>
  </ul>

  <h4>2) Fieldset pour les questions “multiple-opt-comments”</h4>
  <p><strong>Script concerné :</strong> bloc 8a “Désactive complètement les commentaires des lignes non cochées”.</p>

  <ul>
    <li>Les éléments <code>div.row.multiple-opt-comments</code> sont convertis en <code>&lt;fieldset role="group"&gt;</code>.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Chaque ligne (case + commentaire) forme un groupe compréhensible par les technologies d’assistance.</li>
    <li>Même logique que les autres types de questions multi-choix.</li>
  </ul>

  <hr>

  <!-- B) REQUIRED -->
  <h3>B. Gestion des attributs <code>required</code> et des champs cachés</h3>

  <h4>1) Suppression des <code>required</code> sur les champs cachés / invisibles</h4>
  <p><strong>Scripts concernés :</strong> “NETTOYAGE DES REQUIRED…” + blocs 4, 4c, 4d, 4e.</p>

  <p><strong>Le script retire automatiquement <code>required</code> sur :</strong></p>
  <ul>
    <li><code>input[type="hidden"][disabled]</code></li>
    <li>Champs “Autre texte” masqués : <code>.ls-js-hidden</code></li>
    <li>Champs dans : <code>fieldset.multiple-opt.mandatory input</code></li>
  </ul>

  <p><strong>Gestion conditionnelle :</strong></p>
  <ul>
    <li>Si la question est visible + mandatory → <code>required</code> est ajouté.</li>
    <li>Si la question est cachée (<code>.ls-hidden</code>, <code>.ls-irrelevant</code>, <code>display:none</code>) → <code>required</code> est retiré.</li>
    <li>Prise en charge spécifique :
      <ul>
        <li><code>.text-long.mandatory</code></li>
        <li><code>.text-short.mandatory</code></li>
        <li><code>.row.text-short</code> / <code>.row.text-long</code></li>
        <li>Tableaux <code>.ls-table-wrapper</code> : une seule radio obligatoire par ligne</li>
      </ul>
    </li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Plus d’erreurs HTML5 sur des champs invisibles (bug courant de LimeSurvey).</li>
    <li>Les lecteurs d’écran ne rencontrent plus de champs “obligatoires” qui ne sont pas visibles.</li>
    <li>Cohérence totale entre ce que voit l’utilisateur et les obligations réelles.</li>
  </ul>

  <h4>2) Required logique pour les groupes radios / checkboxes</h4>
  <p><strong>Scripts concernés :</strong> blocs 4, 4d, 8a.</p>

  <ul>
    <li>Le <code>required</code> est géré au niveau du <strong>groupe</strong>, pas des inputs individuels.</li>
    <li>Dans les tableaux : une <strong>radio obligatoire par ligne</strong>.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Moins de bruit pour les lecteurs d’écran (pas 10 radios annoncées comme obligatoires).</li>
    <li>Les messages d’erreur s’affichent au niveau de la question → plus naturel.</li>
  </ul>

  <hr>

  <!-- C) DATES -->
  <h3>C. Accessibilité des dates et des champs formatés</h3>

  <h4>1) Dates Jour / Mois / Année + input date caché</h4>
  <p><strong>Scripts concernés :</strong> bloc 1) + 1b).</p>

  <ul>
    <li>L’<code>input[type="date"]</code> de LimeSurvey est :
      <ul>
        <li><code>disabled</code></li>
        <li><code>aria-hidden="true"</code></li>
        <li><code>tabindex="-1"</code></li>
        <li>sans <code>required</code></li>
      </ul>
    </li>
    <li>La date réelle est générée via les sélecteurs :
      <code>&lt;select class="day"&gt;</code>,
      <code>&lt;select class="month"&gt;</code>,
      <code>&lt;select class="year"&gt;</code>.
    </li>
    <li>En cas d’erreur → focus sur le premier select vide.</li>
    <li>Placeholders ajoutés : “Jour”, “Mois”, “Année”.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Focus uniquement sur des éléments visibles → meilleure accessibilité clavier.</li>
    <li>Structure plus claire pour les lecteurs d’écran (3 champs explicites).</li>
    <li>Message d’erreur précis et compréhensible.</li>
  </ul>

  <h4>2) Masquage des calendriers natifs doublons</h4>
  <p><strong>Script concerné :</strong> bloc 5).</p>

  <ul>
    <li>Masquage des composants :
      <code>.input-group-addon i.fa-calendar</code>,
      <code>.tempus-dominus-widget</code>,
      <code>.date-container</code>
    </li>
  </ul>

  <p><strong>Bénéfice :</strong></p>
  <ul>
    <li>Aucun double calendrier perturbant la navigation clavier ou assistée.</li>
  </ul>

  <h4>3) Auto-type pour email, téléphone, nombre et date</h4>
  <p><strong>Script concerné :</strong> bloc 6).</p>

  <ul>
    <li>Selon la classe du conteneur :
      <ul>
        <li><code>.email</code> → <code>type="email"</code> + <code>autocomplete="email"</code></li>
        <li><code>.tel</code> → <code>type="tel"</code> + clavier numérique mobile</li>
        <li><code>.num</code> / <code>.numeric</code> → <code>type="number"</code></li>
        <li><code>.date</code> → <code>type="date"</code></li>
      </ul>
    </li>
    <li>Placeholders adaptés (ex : “prenom.nom@organisme.fr”).</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Clavier mobile adapté (email, téléphone, numérique).</li>
    <li>Validation native plus propre (format, chiffres…).</li>
    <li>Expérience plus fluide sur smartphone et tablette.</li>
  </ul>

</section>
<section id="ameliorations-accessibilite-suite" style="max-width:900px;margin:auto;line-height:1.6;font-size:1.05rem;">

  <!-- D) AUTRE -->
  <h3>D. Gestion intelligente des options “Autre” et champs commentaires</h3>

  <h4>1) Radios “Autre” (value="-oth-")</h4>
  <p><strong>Script concerné :</strong> bloc 7.1</p>
  <ul>
    <li>Le champ texte “Autre” (<code>.other-text-item</code>) est masqué :
      <ul>
        <li>ajout de <code>.ls-hidden</code></li>
        <li><code>aria-hidden="true"</code></li>
        <li><code>disabled</code> sur les champs internes</li>
      </ul>
    </li>
    <li>Le champ n’apparaît que si l’option radio “Autre” est cochée.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Les lecteurs d’écran n’annoncent plus de champs textes inutiles.</li>
    <li>Comportement naturel : zone texte uniquement si “Autre” est choisi.</li>
  </ul>

  <h4>2) Checkboxes “Autre” dans les multiple-opt</h4>
  <p><strong>Script concerné :</strong> bloc 7.2</p>

  <ul>
    <li>Lorsque la case “Autre” est cochée ⇒ le champ texte associé devient visible et actif.</li>
    <li>Lorsque l’utilisateur écrit dans la zone texte ⇒ la case “Autre” se coche automatiquement.</li>
    <li>Lorsque la case est décochée ⇒ le champ texte redevient masqué + disabled.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Synchronisation parfaite entre la case et le champ texte.</li>
    <li>Zéro confusion : champ activé uniquement lorsque pertinent.</li>
  </ul>

  <h4>3) Désactivation complète de “Autre” dans certaines list-radio mandatory</h4>
  <p><strong>Script concerné :</strong> bloc 7.3</p>

  <ul>
    <li>Masquage complet de la ligne “Autre”.</li>
    <li>Désactivation du champ texte associé :
      <ul>
        <li><code>disabled</code></li>
        <li><code>aria-disabled="true"</code></li>
        <li>suppression de <code>required</code></li>
      </ul>
    </li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Évite d’imposer une option “Autre” alors que le questionnaire ne l’utilise finalement pas.</li>
  </ul>

  <h4>4) Affichage forcé des list-with-comment mandatory</h4>
  <p><strong>Script concerné :</strong> bloc 7.4</p>

  <ul>
    <li>Suppression de :
      <ul>
        <li><code>.ls-hidden</code></li>
        <li><code>.ls-irrelevant</code></li>
        <li>attribut <code>hidden</code></li>
      </ul>
    </li>
    <li>Affichage forcé du <code>&lt;fieldset&gt;</code>.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Empêche la situation où une question obligatoire serait cachée (bug LimeSurvey corrigé).</li>
  </ul>

  <h4>5) Multiple-opt-comments : activation des commentaires uniquement pour les lignes cochées</h4>
  <p><strong>Script concerné :</strong> bloc 8a</p>

  <ul>
    <li>Si aucune case n’est cochée ⇒ champs commentaires visibles mais <strong>non obligatoires</strong>.</li>
    <li>Si une case est cochée ⇒ <strong>seul le commentaire de cette ligne devient obligatoire</strong>.</li>
    <li>Les autres commentaires sont désactivés (disabled + aria-disabled).</li>
    <li>Interception de l’événement <code>invalid</code> pour éviter les erreurs sur les lignes non cochées.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Plus d’erreurs absurdes sur des commentaires appartenant à des lignes non sélectionnées.</li>
    <li>Logique parfaitement compréhensible pour les utilisateurs et lecteurs d’écran.</li>
  </ul>

  <hr>

  <!-- E) ARIA-LIVE -->
  <h3>E. Messages d’alerte, aria-live et feedback utilisateur</h3>

  <h4>1) Zone aria-live discrète pour les messages système</h4>
  <p><strong>Script concerné :</strong> bloc 7.5</p>

  <ul>
    <li>Création d’un élément caché avec :
      <ul>
        <li><code>aria-live="polite"</code></li>
        <li><code>aria-atomic="true"</code></li>
      </ul>
    </li>
    <li>Annonce “Votre formulaire est en cours de traitement” au clic sur Envoyer.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Retour vocal rassurant pour les lecteurs d’écran.</li>
    <li>Évite les doubles clics paniqués.</li>
  </ul>

  <h4>2) Modal d’alerte Bootstrap : aria-live dynamique</h4>
  <p><strong>Script concerné :</strong> bloc 7.6</p>

  <ul>
    <li>Lorsque la modal s’ouvre :
      <ul>
        <li><code>aria-live="assertive"</code></li>
        <li><code>aria-atomic="true"</code></li>
      </ul>
    </li>
    <li>Lorsque la modal se ferme :
      <ul>
        <li>Suppression de ces attributs.</li>
      </ul>
    </li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Les messages importants sont annoncés au bon moment.</li>
    <li>Évite des annonces inutiles lorsque la modal n’est pas visible.</li>
  </ul>

  <h4>3) Message final de confirmation</h4>
  <ul>
    <li>Ajout d’un message avec <code>role="alert"</code> indiquant :  
      <strong>“Vos réponses ont bien été enregistrées.”</strong></li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Rassure les utilisateurs.</li>
    <li>Annonce claire pour les lecteurs d’écran.</li>
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

  <!-- F) VALIDATION -->
  <h3>F. Validation séquentielle et gestion de la touche Entrée</h3>

  <h4>1) Validation question par question</h4>
  <p><strong>Script concerné :</strong> bloc 8)</p>

  <ul>
    <li>Suppression des bulles HTML5 natives (<code>novalidate</code>).</li>
    <li>Détection de la première question en erreur.</li>
    <li>Message d’erreur inséré près du <code>&lt;legend&gt;</code> :
      <ul>
        <li><code>role="alert"</code></li>
        <li><code>aria-live="assertive"</code></li>
      </ul>
    </li>
    <li>Focus automatique sur l’élément fautif.</li>
    <li>Scroll centré sur la question.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Beaucoup plus clair pour l’utilisateur.</li>
    <li>Messages adaptés : format email, longueur, pattern…</li>
    <li>Aide parfaite pour NVDA, JAWS, VoiceOver.</li>
  </ul>

  <h4>2) Gestion de la touche Entrée</h4>
  <ul>
    <li>La touche Entrée reproduit l’action “Suivant / Envoyer”.</li>
    <li>Ignorée sur les textarea, éditeurs riche, contenteditable.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Navigation clavier extrêmement fluide.</li>
    <li>Évite des envois accidentels.</li>
  </ul>

  <hr>

  <!-- G) FOCUS -->
  <h3>G. Styles de focus radio/checkbox</h3>

  <p><strong>Script concerné :</strong> bloc final “applyChoiceFocusStyles”</p>

  <ul>
    <li>Ajout de la classe <code>.ls-radio-focus</code> lors du focus clavier.</li>
    <li>Suppression lors du blur.</li>
    <li>CSS associé :
      <ul>
        <li>outline visible</li>
        <li>contour renforcé</li>
        <li>fond légèrement coloré</li>
      </ul>
    </li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Repérage immédiat du focus au clavier.</li>
    <li>Indispensable pour l’accessibilité WCAG / RGAA.</li>
  </ul>

  <hr>

  <!-- H) LANDMARKS -->
  <h3>H. Landmarks HTML, contraste et couleurs</h3>

  <ul>
    <li>Ajout des balises structurantes :
      <ul>
        <li><code>&lt;header role="banner"&gt;</code></li>
        <li><code>&lt;main role="main"&gt;</code></li>
        <li><code>&lt;footer role="contentinfo"&gt;</code></li>
      </ul>
      (non présents nativement dans LimeSurvey)
    </li>
    <li>Corrections de contrastes insuffisants (texte, icônes, bordures).</li>
    <li>Amélioration des couleurs pour respecter les ratios WCAG.</li>
  </ul>

  <p><strong>Bénéfices :</strong></p>
  <ul>
    <li>Structure de page claire pour les lecteurs d’écran.</li>
    <li>Mieux conforme RGAA 4 / WCAG 2.1.</li>
    <li>Confort général renforcé.</li>
  </ul>

</section>
