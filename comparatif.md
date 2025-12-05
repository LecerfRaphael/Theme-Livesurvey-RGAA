  <!-- 1. Structure de page : rôle main / header -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Structure de page : rôle <code>main</code> / <code>header</code></strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Le contenu principal est dans un
          <code>&lt;article&gt;</code> sans rôle explicite, le header
          de la navigation n’est pas clairement structuré.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Tu introduis <code>&lt;header role="banner"&gt;</code> et
          <code>&lt;main role="main"&gt;</code>. Le contenu du questionnaire est
          clairement identifié comme zone principale.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 9.1 / 6.1.1</strong> – zones de page repérables ;
          <strong>WCAG 2.0 – 1.3.1 / 2.4.1</strong> (landmarks).
        </p>
      </div>
    </div>
  </div>

  <!-- 2. Titre de page dynamique -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Titre de page dynamique (meta <code>&lt;title&gt;</code>)</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Le <code>&lt;title&gt;</code> est statique :
          « Enquête recensemment… (test finalisation template) ». Aucun lien
          avec la page courante ni le groupe affiché.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Script JavaScript qui recalcule <code>document.title</code> :
          « Enquête recensement et cartographie RAN — Page X / Y », en
          récupérant le nom de l’enquête et du groupe. Mise à jour aussi des
          metas OpenGraph / Twitter.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 8.9 / 8.10</strong> – titres de pages pertinents ;
          <strong>WCAG 2.4.2 Page Titled</strong>.
        </p>
      </div>
    </div>
  </div>

  <!-- 3. Titre visuel de page -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Titre visuel de page (<code>ls-page-title</code>)</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Le H1 de groupe est géré par le thème, mais sans indication du
          numéro de page dans l’enchaînement global (ou alors sans cohérence).
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Script qui recalcule le H1 : « Enquête… — Page 1 / 1 » en analysant
          l’index des questions / valeurs <code>move</code>. Meilleure
          compréhension pour tous, y compris lecteurs d’écran.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 9.1 / 8.10</strong>,
          <strong>WCAG 2.4.2 / 2.4.6</strong>.
        </p>
      </div>
    </div>
  </div>

  <!-- 4. Index des questions -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Index des questions (menu de navigation)</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Lien <code>&lt;a class="dropdown-toggle"&gt;</code> sans texte caché
          supplémentaire ni <code>sr-only</code>. Toggler mobile sans
          indication vocale (« Menu » absent).
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Tu transformes l’index en
          <code>&lt;button class="btn-nostyle dropdown-toggle nav-link"&gt;</code>
          + ajout d’un <code>&lt;span class="sr-only"&gt;Menu&lt;/span&gt;</code>
          dans le toggler. Comportement plus clair pour lecteurs d’écran et
          activation clavier mieux cadrée.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 9.2 / 9.3</strong>,
          <strong>WCAG 2.1.1 Keyboard</strong>, 2.4.7 Focus Visible.
        </p>
      </div>
    </div>
  </div>

  <!-- 5. Texte obligatoire / astérisque -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Texte obligatoire / astérisque</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Astérisque + phrase « (Cette question est obligatoire) » dans un
          <code>&lt;span class="visually-hidden"&gt;</code> – déjà correct,
          mais répété dans chaque bloc avec un H2/H3 plutôt verbeux.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Tu gardes le couple astérisque +
          <code>span.visually-hidden</code>, mais tu ajoutes un rappel
          global dans le groupe : <code>&lt;sup&gt;</code> + « question
          obligatoire ». Le pattern est plus lisible et évite la redondance
          textuelle.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 8.2 / 11.1</strong>,
          <strong>WCAG 3.3.2 Labels or Instructions</strong>.
        </p>
      </div>
    </div>
  </div>

  <!-- 6. Questions textuelles : label vs div -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Questions textuelles : <code>label</code> vs <code>div</code></strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Texte de question dans
          <code>&lt;div class="question-title-container"&gt;&lt;div class="ls-label-question"&gt;…&lt;/div&gt;</code>
          et champ avec <code>aria-labelledby</code>. Pas de vrai
          <code>&lt;label for="…"&gt;</code> direct : dépend du couplage ARIA.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Tu remplaces par un vrai
          <code>&lt;label class="ls-label-question" for="answer…" /&gt;</code>
          (le <code>id</code> de l’input), qui joue le rôle à la fois visuel
          et programmatique. L’ARIA <code>aria-labelledby</code> reste cohérent.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 11.1</strong> – chaque champ a une étiquette ;
          <strong>WCAG 1.3.1 / 3.3.2</strong>.
        </p>
      </div>
    </div>
  </div>

  <!-- 7. Structure des questions (fieldset / legend) -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Structure des questions (<code>fieldset</code> / <code>legend</code>)</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Questions sous forme de <code>div.question-container</code>
          avec sous-blocs internes. Pour les listes radio, le « titre »
          est dans un bloc <code>div</code> séparé, pas dans un
          <code>&lt;legend&gt;</code>.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Tu appliques un script générique : transformation de
          <code>div.list-radio</code>, <code>div.multiple-opt</code>,
          <code>div.numeric-multi</code>, <code>div.date</code>, etc. en
          <code>&lt;fieldset class="question-container …"&gt;</code> +
          <code>&lt;legend class="ls-label-question"&gt;</code>.
          Structuration sémantique complète.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 9.2</strong>,
          <strong>WCAG 1.3.1</strong> – relations logiques & regroupements de champs.
        </p>
      </div>
    </div>
  </div>

  <!-- 8. Messages d’aide / erreurs -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Gestion des messages d’aide / erreurs (<code>question-valid-container</code>)</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Les messages d’erreur / aide sont dans
          <code>div.question-valid-container</code> avec
          <code>role="alert"</code> sur <code>.ls-questionhelp</code>,
          même quand il s’agit de simples tips. Risque de verbosité
          « alerte » pour JAWS / NVDA.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Script qui retire <code>role="alert"</code> et convertit en
          <code>aria-live="polite"</code> ; suppression des
          <code>question-valid-container</code> superflus. Les aides
          deviennent des messages d’information, pas des alertes intempestives.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 7.1 / 7.2</strong>,
          <strong>WCAG 3.3.1 Error Identification</strong>, 4.1.3 Status Messages.
        </p>
      </div>
    </div>
  </div>

  <!-- 9. Conditionnel / pertinence -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Conditionnel / pertinence (<code>ls-irrelevant</code> / <code>ls-hidden</code>)</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Quand une question redevient pertinente, l’Expression Manager enlève
          <code>ls-irrelevant</code> mais laisse parfois
          <code>ls-hidden</code> / <code>hidden</code> /
          <code>display:none</code>, ce qui bloque la navigation pour
          clavier / lecteur d’écran.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Script 4f) : <code>unhideIfRelevant(q)</code> enlève
          <code>ls-hidden</code>, <code>hidden</code>,
          <code>display:none</code> dès que la question redevient
          pertinente (sauf si marquée
          <code>data-ls-manual-hide="1"</code>). Les questions
          conditionnelles redeviennent visibles correctement.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 10.7 / 12.13</strong>,
          <strong>WCAG 1.3.1</strong> (contenu contrôlé par scripts) &amp; 2.1.1.
        </p>
      </div>
    </div>
  </div>

  <!-- 10. Questions « Si oui… » -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Questions « Si oui… » (logique conditionnelle lisible)</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Logique de pertinence gérée uniquement via Expression Manager
          (conditions internes). Pas de cohérence sémantique explicite
          entre la question mère (« Oui / Non ») et la question fille (qui suit).
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Script 4g) : détection des <code>&lt;legend&gt;</code> commençant
          par « Si oui », recherche de la question parente juste au-dessus,
          écoute des radios « Oui » et masquage / ré-affichage propre de la
          question fille, avec nettoyage des réponses si masquée.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 10.7</strong>,
          <strong>WCAG 3.2.2 On Input</strong> – changements de contexte prévisibles + 3.3.2.
        </p>
      </div>
    </div>
  </div>

  <!-- 11. Required conditionnel -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Required conditionnel (visibilité / pertinence)</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Les champs dans des questions <code>mandatory</code> restent
          parfois <code>required</code> même si cachés (cas
          <code>.ls-hidden</code>, conditionnels, <code>othertext</code>, etc.),
          ce qui bloque la validation.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Bloc 4) : plusieurs scripts qui gèrent <code>required</code>
          uniquement sur questions visibles : text-short / text-long,
          list-radio, tableaux <code>.ls-table-wrapper</code>,
          multiple-opt, etc. Nettoyage des champs masqués.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 11.1 / 10.7</strong>,
          <strong>WCAG 3.3.1 / 3.3.3</strong> – erreurs identifiées et formulaires utilisables.
        </p>
      </div>
    </div>
  </div>

  <!-- 12. Entrées « Autre : » -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Entrées « Autre : » (<code>othertext</code>)</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Le champ « Autre : » a parfois un <code>required</code> ou
          influence la validation de façon bancale (obligatoire même sans
          choix « Autre »).
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Nettoyage du <code>required</code> sur
          <code>.ls-js-hidden input.othertext</code> + logique :
          le message « préciser le champ ‘Autre’ » ne s’active que si
          l’option <code>-oth-</code> est sélectionnée et que le champ texte
          est vide.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 11.1</strong>,
          <strong>WCAG 3.3.2</strong> – étiquettes &amp; aides adaptées.
        </p>
      </div>
    </div>
  </div>

  <!-- 13. Champs numériques / type de clavier -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Champs numériques / type de clavier (mobile)</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Tous les champs sont en <code>type="text"</code> même pour
          numérique, téléphone, mail, date ; cela limite l’ergonomie clavier
          virtuel et les contrôles natifs.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Script 6) : conversion automatique en <code>type="email"</code>,
          <code>type="tel"</code>, <code>type="number"</code>,
          <code>type="date"</code> selon la classe du fieldset
          (<code>.email</code>, <code>.tel</code>, <code>.num</code>,
          <code>.numeric</code>, <code>.date</code>), avec gestion d’inputmode
          / placeholder.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 7.5</strong>,
          <strong>WCAG 2.1.1 / 2.5.1</strong> – facilité d’usage au clavier & sur mobile.
        </p>
      </div>
    </div>
  </div>

  <!-- 14. Champs date : trio jour/mois/année -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Champs date : trio jour/mois/année + input caché</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Input <code>type="date"</code> masqué + selects jour / mois / année,
          mais liaison parfois fragile, validations peu explicites ; risque de
          focus sur le champ caché en cas d’erreur.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Bloc 1) : script qui synchronise les selects J/M/A vers l’input
          <code>type="date"</code> caché, enlève <code>required</code> sur ce
          dernier, gère le focus vers le premier select vide en cas d’erreur,
          + placeholders « Jour / Mois / Année ».
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 3.2 / 11.1</strong>,
          <strong>WCAG 1.3.1 / 3.3.1</strong> – sens conservé, erreurs identifiables.
        </p>
      </div>
    </div>
  </div>

  <!-- 15. Callout JS désactivé -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Callout JavaScript désactivé</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Message JavaScript déjà présent (« JavaScript désactivé… »), mais
          l’impact sur le fonctionnement n’est pas clarifié, et pas forcément
          mis à jour avec les évolutions.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Le message est conservé, ton pack ajoute des scripts mais tu veilles
          à ce que la structure HTML reste fonctionnelle sans JS (labels,
          fieldsets, required côté serveur, etc.). L’expérience est dégradée
          mais reste utilisable.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 8.9 / 13.1</strong>,
          <strong>WCAG 1.3.1 / 2.1.1</strong> – fonctionnement sans script.
        </p>
      </div>
    </div>
  </div>

  <!-- 16. Visibilité des pickers calendrier -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Visibilité des pickers calendrier</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Les pickers graphiques (<code>.input-group-addon i.fa-calendar</code>,
          widgets tempus dominus) peuvent introduire du bruit et des pièges de
          navigation pour lecteurs d’écran.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Bloc 5) : masquage des <code>.input-group-addon</code> avec icône
          calendrier et des widgets <code>.tempus-dominus-widget</code>,
          <code>.date-container</code>. Reste la saisie via selects ou champs date.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 7.5 / 10.7</strong>,
          <strong>WCAG 2.1.1 / 2.4.3</strong> – suppression de contrôles redondants ou confus.
        </p>
      </div>
    </div>
  </div>

  <!-- 17. Hiérarchie des titres / légendes de groupe -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Hiérarchie des titres / légendes de groupe</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Groupes : titre « Identification » dans un
          <code>&lt;div class="group-title h3"&gt;</code> sans relation forte
          avec la page / structure globale.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          <code>&lt;fieldset&gt;</code> de groupe avec
          <code>&lt;legend class="group-title h3"&gt;Identification&lt;/legend&gt;</code>,
          H1 distinct pour le titre général + page. Hiérarchie claire :
          H1 (enquête/page), legend (bloc de questions).
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 9.1 / 9.2</strong>,
          <strong>WCAG 1.3.1 / 2.4.6</strong>.
        </p>
      </div>
    </div>
  </div>

  <!-- 18. Compatibilité lecteur d’écran : aide / erreurs -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Compatibilité lecteur d’écran : texte d’aide et messages d’erreur</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Les messages d’erreurs sont parfois trop nombreux, annoncés comme
          <code>role="alert"</code>, avec peu de distinction entre aide,
          astuce et erreur réelle.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Tu standardises les <code>.ls-questionhelp</code> en infos non
          bloquantes (<code>aria-live="polite"</code>), et les vrais cas
          d’erreurs restent gérés par la validation EM. Résultat : synthèse
          vocale moins saturée.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 7.1 / 7.2</strong>,
          <strong>WCAG 3.3.1</strong>.
        </p>
      </div>
    </div>
  </div>

  <!-- 19. Gestion dynamique des questions dans les tableaux -->
  <div class="critere-card">
    <h2 class="h4 critere-title">
      <strong>Gestion dynamique des questions dans les tableaux</strong>
    </h2>
    <div class="row">
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version de base</div>
        <p>
          Tables d’items (<code>.ls-table-wrapper</code>) : la validation EM
          exige parfois une réponse par ligne mais sans véritable couplage
          <code>required</code> HTML.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Version améliorée</div>
        <p>
          Script de validation par ligne (4b) qui ajoute ou enlève
          <code>required</code> en fonction de la sélection au niveau de chaque
          ligne. Meilleure cohérence client / serveur.
        </p>
      </div>
      <div class="col-md-4 mb-3">
        <div class="critere-col-title">Références RGAA / WCAG</div>
        <p class="critere-ref">
          <strong>RGAA 11.1</strong>,
          <strong>WCAG 3.3.1 / 3.3.3</strong>.
        </p>
      </div>
    </div>
  </div
