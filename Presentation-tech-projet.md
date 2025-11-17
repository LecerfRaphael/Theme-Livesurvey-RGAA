<section id="ameliorations-accessibilite" style="max-width:900px;margin:auto;line-height:1.6;font-size:1.05rem;">

  <h2>1. Détail des améliorations pour l’accessibilité</h2>
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
        <li><code>&lt;header&gt;</code></li>
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
