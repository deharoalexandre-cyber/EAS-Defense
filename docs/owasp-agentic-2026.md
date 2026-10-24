# OWASP Agentic 2026 — cartographie détaillée d'EAS Défense

[English](owasp-agentic-2026.en.md) · [Présentation EAS](../README.md) · [Architecture](architecture.md) · [Qualifications](evidence.md)

**État documentaire : 15 octobre 2026.** Cette cartographie rapproche les dix familles du [Top 10 OWASP pour les applications agentiques 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) de **86 mesures suivies par Elyne Corp**. Les identifiants `ASIxx.n`, les libellés français des mesures et les statuts sont notre découpage interne : OWASP ne délivre pas ce score et ne certifie pas EAS.

La colonne historique décrit **R14 au 8 octobre** ; la colonne relue est un **inventaire de preuves multi-versions observées en laboratoire jusqu'à R48**. R45 est le candidat Windows de référence ; R48 est un essai d'accès fichier sur la lignée R42/R43, après pose des ACL par l'installateur de laboratoire corrigé R46. Cette colonne n'établit pas que les 26 validations ont toutes été rejouées sur le même build R45, sur un agent tiers complet ou chez un client.

## Lire les statuts

| Statut interne | Sens appliqué à chaque ligne |
| --- | --- |
| **V — validée dans un périmètre borné** | Un effet a été observé dans un scénario nommé. La justification indique ce que l'essai laisse ouvert. |
| **P — partielle** | Un mécanisme ou une atténuation existe, mais la preuve de bout en bout ou la portée de la mesure reste incomplète. |
| **R — à réaliser** | Une fonction, un raccordement ou une recette nécessaire reste à faire. |
| **O — organisationnelle** | Le résultat dépend aussi d'une procédure ou d'une décision de l'exploitant. |

**Trois lectures distinctes :** les dix catégories ont au moins une atténuation identifiée ; **26/86** lignes ont un effet direct validé dans leur périmètre ; aucune catégorie n'est qualifiée intégralement. Les portes Red P0 et les scores de campagne sont des protocoles différents et ne se déduisent pas de ce tableau. Les essais P0 restés `INCONCLUSIVE` ne deviennent pas des `PASS` par un reclassement OWASP.

## Répartition par catégorie

| Catégorie OWASP | Mesures internes | V | P | R | O |
| --- | ---: | ---: | ---: | ---: | ---: |
| [ASI01 — Détournement de l'objectif de l'agent](#asi01) | 9 | 2 | 5 | 1 | 1 |
| [ASI02 — Détournement et abus des outils](#asi02) | 8 | 4 | 3 | 1 | 0 |
| [ASI03 — Abus d'identité et de privilèges](#asi03) | 9 | 1 | 7 | 0 | 1 |
| [ASI04 — Chaîne d'approvisionnement agentique](#asi04) | 9 | 2 | 6 | 1 | 0 |
| [ASI05 — Exécution imprévue de code](#asi05) | 7 | 2 | 5 | 0 | 0 |
| [ASI06 — Empoisonnement de la mémoire et du contexte](#asi06) | 9 | 2 | 4 | 3 | 0 |
| [ASI07 — Communications interagents non sûres](#asi07) | 9 | 5 | 3 | 1 | 0 |
| [ASI08 — Défaillances en cascade](#asi08) | 10 | 4 | 4 | 2 | 0 |
| [ASI09 — Manipulation de la confiance humaine](#asi09) | 9 | 1 | 6 | 1 | 1 |
| [ASI10 — Agents incontrôlés](#asi10) | 7 | 3 | 4 | 0 | 0 |
| **Total** | **86** | **26** | **47** | **10** | **3** |

## Ce qui a changé depuis la grille R14

La relecture applique le même seuil de preuve aux 86 lignes. **19 statuts changent** : 17 passages vers V (dont un R→V), et deux passages R→P. Les autres justifications ont été relues sans changement de statut. Le total passe de **9 V / 61 P / 13 R / 3 O** à **26 V / 47 P / 10 R / 3 O**. Chaque reclassement désigne une observation bornée sur sa version, jamais une garantie universelle.

| Mesure interne | R14 | Inventaire relu |
| --- | :---: | :---: |
| ASI01.2 — Droits minimaux et validation des actions sensibles | P | **V** |
| ASI02.1 — Profils minimaux par outil et périmètre de données | P | **V** |
| ASI02.3 — Isolation des exécuteurs et filtrage des sorties réseau | R | **V** |
| ASI03.1 — Droits restreints et temporaires par tâche | R | **P** |
| ASI03.3 — Autorisation centralisée à chaque étape privilégiée | P | **V** |
| ASI04.5 — Authentification mutuelle et messages signés | P | **V** |
| ASI04.6 — Vérification continue des composants et comportements | P | **V** |
| ASI05.2 — Séparer l’agent des systèmes de production | R | **P** |
| ASI07.1 — Canaux chiffrés et authentification mutuelle | P | **V** |
| ASI07.2 — Intégrité du contenu et du contexte | P | **V** |
| ASI07.3 — Antirejeu lié au contexte et au temps | P | **V** |
| ASI07.4 — Refus des modes faibles et contrôle des capacités | P | **V** |
| ASI07.9 — Contrats typés et audience explicite | P | **V** |
| ASI08.1 — Conception tolérant l’indisponibilité des composants | P | **V** |
| ASI08.2 — Isolation, segmentation et interfaces restreintes | P | **V** |
| ASI08.7 — Limites d’impact et mécanismes de coupure | P | **V** |
| ASI10.1 — Gouvernance et traces des interactions/actions | P | **V** |
| ASI10.2 — Zones de confiance et isolation restrictive | P | **V** |
| ASI10.4 — Arrêt, révocation et quarantaine rapide | P | **V** |

## Les 86 mesures et leurs limites

Les repères de preuve renvoient à des rapports internes datés ; seuls des résumés expurgés figurent dans ce dépôt. Les reçus natifs, politiques, configurations et chemins du laboratoire ne sont pas publiés. [Les résultats R43, R44, R45 et R48 sont résumés ici](evidence.md). Une ligne sans repère de release décrit un mécanisme ou un travail restant, et ne revendique pas de nouvel essai.

<a id="asi01"></a>

### ASI01 — Détournement de l'objectif de l'agent

| Repère interne | Mesure suivie | R14 | Relecture | Observation et limite | Repères de preuve |
| --- | --- | :---: | :---: | --- | --- |
| ASI01.1 | Entrées en langage naturel non fiables | P | **P** | Quatre injections R10 sont bloquées ou mises en quarantaine ; le message propre du même lot est aussi bloqué faute de contrat. Sans témoin positif enrôlé, l’effet propre du filtre reste partiel. | R10 |
| ASI01.2 | Droits minimaux et validation des actions sensibles | P | **V** | Bonsaï R13 : écriture directe refusée sous SID LocalService, fichier intact ; outil EAS autorisé puis dépôt restauré. Preuve bornée au parcours code testé. | R13 |
| ASI01.3 | Objectifs et instructions système sous contrôle de changement | P | **P** | Fichiers déclarés surveillés par Cyber ; workflow de changement d’objectif à formaliser. | — |
| ASI01.4 | Contrôle des changements d’intention avant effet | P | **P** | Politique et détection de séquences ; comparaison à un objectif métier approuvé à ajouter. | — |
| ASI01.5 | Évaluer une enveloppe signée liant but et contraintes | R | **R** | Les preuves d’action existent ; une capsule d’objectif par cycle n’est pas implémentée. | — |
| ASI01.6 | Contrôle de toutes les sources de contexte | P | **P** | Filtres mémoire/RAG/A2A ; R25 trace un chunk FTS synthétique par ID et empreinte. Connecteurs métier, ingestion client et provenance générale restent à recetter. | R25 |
| ASI01.7 | Journalisation et suivi de la dérive d’objectif | P | **P** | Événements et séquences suivis ; identifiant stable d’objectif et baseline métier à compléter. | — |
| ASI01.8 | Campagnes adverses périodiques et reprise | V | **V** | Campagnes Red répétées R12–R14 puis R20/R21B ; R21B : 19/19 jobs défendus et 9/52 étapes indéterminées. La périodicité chez l’exploitant reste à organiser. | R14, R20, R21B |
| ASI01.9 | Intégration au dispositif de menace interne | O | **O** | Procédure, responsable, signalements et exercices relèvent aussi de l’organisme exploitant. | — |

<a id="asi02"></a>

### ASI02 — Détournement et abus des outils

| Repère interne | Mesure suivie | R14 | Relecture | Observation et limite | Repères de preuve |
| --- | --- | :---: | :---: | --- | --- |
| ASI02.1 | Profils minimaux par outil et périmètre de données | P | **V** | Le lecteur EAS R15 lit 69 octets autorisés et subit un refus Windows sur canari ; R18 lie l’appel à l’identité Acta. Validation bornée à cet outil et ce profil. | R15, R18 |
| ASI02.2 | Authentification et approbation de chaque action sensible | P | **P** | Jeton interne et politique du broker ; autorisation éphémère liée à l’effet à compléter. | — |
| ASI02.3 | Isolation des exécuteurs et filtrage des sorties réseau | R | **V** | Le worker de code R20/R21 est AppContainer/Job : refus réseau avec témoin positif, enfant Low au même SID et canaris refusés. R48 observe sur une lignée R42/R43 distincte deux accès fichier permis et deux refusés après pose des ACL par l'installateur de laboratoire corrigé R46. V reste limité au worker qualifié ; tous les outils enregistrés ne sont pas isolés. | R20, R21, R42, R43, R44, R45, R48 |
| ASI02.4 | Contrôle d’intention et des paramètres avant exécution | V | **V** | Contrôle avant effet démontré sur chemins réels : décision de politique, refus direct, reçus outil/applier et corrélation audit sur le tir natif Bonsaï R13. | R13 |
| ASI02.5 | Budgets et limitation des usages | P | **P** | Quotas d’appels présents ; plafonds de coût/tokens et budgets persistants à compléter. | — |
| ASI02.6 | Identifiants temporaires liés à la session | R | **R** | Les jetons internes actuels ne sont pas des capacités à usage unique par invocation. | — |
| ASI02.7 | Résolution non ambiguë et version des outils | P | **P** | Identifiants exacts du registre ; versions/empreintes des connecteurs à vérifier avant activation. | — |
| ASI02.8 | Traçabilité des appels et détection des dérives | V | **V** | Reçus Red/EAS/Cyber corrélés et ledger vérifié ; R21B garde 9 étapes indéterminées malgré 19/19 jobs défendus. La filiation métier complète reste hors preuve. | R14, R21B |

<a id="asi03"></a>

### ASI03 — Abus d'identité et de privilèges

| Repère interne | Mesure suivie | R14 | Relecture | Observation et limite | Repères de preuve |
| --- | --- | :---: | :---: | --- | --- |
| ASI03.1 | Droits restreints et temporaires par tâche | R | **P** | R42–R45 observent des droits OS restreints par profil EAS signé, un jeton AppContainer Low, des refus ciblés et l'arrêt du processus. R48 ajoute deux accès fichier permis et deux refusés sur la lignée R42/R43, après pose des ACL par l'installateur de laboratoire corrigé R46. Durée courte et liaison à chaque tâche non qualifiées. | R42, R43, R44, R45, R48 |
| ASI03.2 | Identités et espaces séparés entre sessions | P | **P** | Identité Windows native R13 ; Acta et profils EAS confinés sur clone R21–R45. Séparation multi-session et de plusieurs agents clients non démontrée. | R13, R21, R42, R45 |
| ASI03.3 | Autorisation centralisée à chaque étape privilégiée | P | **V** | R24 : write/read/check/run d’une conversation Acta passent par ToolBroker et quatre audits os_worker ; R13 refuse la voie directe. V limité au parcours code raccordé. | R13, R24 |
| ASI03.4 | Approbation humaine des élévations | P | **P** | Revue de confinement durable ; approbation de chaque élévation métier à compléter. | — |
| ASI03.5 | Liaison du jeton à l’identité, l’audience, le but et la session | P | **P** | Messages A2A liés au contenu/destinataire/session ; jetons outils non liés à un but signé. | — |
| ASI03.6 | Évaluer la gestion centralisée des identités d’agents | O | **O** | Choix et intégration AD/Entra/autre à définir avec l’environnement de recette. | — |
| ASI03.7 | Droits par ressource, finalité et durée ; révocation | P | **P** | Registre et révocation persistante ; changement de contexte et expiration par tâche à compléter. | — |
| ASI03.8 | Détection des délégations de privilèges | P | **P** | Contrats et contrôles A2A ; chaînes de délégation sur le système cible à éprouver. | — |
| ASI03.9 | Détection des élévations et réemplois de jetons hors contexte | P | **P** | Signaux d’usurpation/rejeu A2A ; télémétrie IAM et flux de type device-code non recettés. | — |

<a id="asi04"></a>

### ASI04 — Chaîne d'approvisionnement agentique

| Repère interne | Mesure suivie | R14 | Relecture | Observation et limite | Repères de preuve |
| --- | --- | :---: | :---: | --- | --- |
| ASI04.1 | Provenance, inventaires SBOM/AIBOM et attestations | P | **P** | Dépendances épinglées/auditées ; SBOM/AIBOM attesté de la livraison à produire. | — |
| ASI04.2 | Sources autorisées et vérification avant installation | P | **P** | R45 vérifie et pose un candidat signé en laboratoire. Le rejet natif d'une source non autorisée par un installateur produit n'a pas été démontré. | R45 |
| ASI04.3 | Construction reproductible et isolation | R | **R** | La signature et la pose de laboratoire sont observées ; aucune construction reproductible bit à bit et attestée indépendamment n'a été démontrée. | R45 |
| ASI04.4 | Instructions et schémas sous revue et contrôle de version | P | **P** | Configuration et code versionnés ; workflow de revue de l’organisme à formaliser. | — |
| ASI04.5 | Authentification mutuelle et messages signés | P | **V** | Vrai TLS : certificat client approuvé accepté, autre AC refusée ; R11 accepte une preuve A2A hybride complète et refuse chaque signature manquante. PKI client et liaison cert↔agent ouvertes. | tests TLS, R11 |
| ASI04.6 | Vérification continue des composants et comportements | P | **V** | R12 : Cyber vivant détecte puis met en quarantaine le canari exact créé et enrôlé par Red, au même SHA-256 ; R35 ajoute la corrélation d’un rejet HPKE. V sur ces objets suivis. | R12, R35 |
| ASI04.7 | Épinglage, déploiement progressif et retour arrière | P | **P** | Fichiers surveillés et restauration bornée ; pipeline de déploiement progressif à établir. | — |
| ASI04.8 | Révocation d’urgence d’un composant compromis | P | **P** | Confinement outils/sessions et révocation de jetons ; diffusion sur plusieurs hôtes non recettée. | — |
| ASI04.9 | Architecture tolérant un composant compromis | P | **P** | R35 installe Cyber sous LocalService ; R36B constate 18 refus d’ouverture de neuf secrets EAS. Handles hérités, voies indirectes et pannes multi-hôtes restent ouverts. | R35, R36B |

<a id="asi05"></a>

### ASI05 — Exécution imprévue de code

| Repère interne | Mesure suivie | R14 | Relecture | Observation et limite | Repères de preuve |
| --- | --- | :---: | :---: | --- | --- |
| ASI05.1 | Validation des sorties et du code proposé | V | **V** | R13 prouve une écriture code réelle médiée et un refus direct ; des tests locaux CodeShield analysent des diffs hostiles. Le lien de bout en bout sur le même diff reste hors preuve. | R13, tests CodeShield |
| ASI05.2 | Séparer l’agent des systèmes de production | R | **P** | R21/R22 confinent le service Acta testé et refusent des accès directs aux secrets EAS ; R42–R45 qualifient des profils EAS signés. Pas de déploiement client/production ni d’agent tiers entier. | R21, R22, R42, R45 |
| ASI05.3 | Interdire les évaluateurs de code dangereux | P | **P** | L’outil lint ne lance pas le code ; inventaire de tous les exécuteurs métier à contrôler. | — |
| ASI05.4 | Compte non privilégié et environnement isolé | P | **P** | AppContainer Low/Job est observé pour des workers et profils ciblés, dont le processus R48 avec accès fichier permis et refusés. R37 relève aussi un groupe Administrators actif chez le client de laboratoire : aucun compte non privilégié général n'est prouvé. | R21, R37, R42, R45, R48 |
| ASI05.5 | Frontières de session et séparation génération/exécution | P | **P** | R21–R25 exercent un profil ASGI Acta confiné ; R42–R45 fournissent un lanceur EAS générique. L’isolation de chaque session et de tous les processus reste à recetter. | R21, R23, R42, R45 |
| ASI05.6 | Approbations et liste d’exécutions autorisées | P | **P** | Registre et revue de zones sensibles ; approbations d’exécutions élevées à ajouter. | — |
| ASI05.7 | Analyse statique, surveillance et traces des exécutions | V | **V** | P0-04 R13 fournit SID natif, reçus outil/applier, audit EAS et restauration de baseline ; couverture native de l’agent de code démontrée. | R13 |

<a id="asi06"></a>

### ASI06 — Empoisonnement de la mémoire et du contexte

| Repère interne | Mesure suivie | R14 | Relecture | Observation et limite | Repères de preuve |
| --- | --- | :---: | :---: | --- | --- |
| ASI06.1 | Chiffrement et accès minimal aux données | P | **P** | mTLS et décisions EAS ; R37–R40 isolent un Store propre à Acta sous une autre identité. Chiffrement au repos et ACL des magasins de tous les agents non qualifiés. | R37, R40 |
| ASI06.2 | Contrôle des contenus avant écriture | V | **V** | P0-03 PASS natif R13 avec Bonsaï réel : écritures mémoire/RAG adverses soumises à EAS, identité effective et restauration vérifiée. | R13 |
| ASI06.3 | Segmentation des mémoires et contextes | P | **P** | R13 valide un chemin mémoire réel ; R40 persiste un échange Acta via un Store distinct. Pas de preuve de segmentation multi-tenant ou de tous les agents. | R13, R40 |
| ASI06.4 | Sources authentifiées et rétention limitée | P | **P** | Frontière du jeton interne ; politiques de rétention par sensibilité à ajouter. | — |
| ASI06.5 | Provenance et détection d’écritures anormales | P | **P** | R25 trace un chunk FTS synthétique entre recherche et filtre EAS par ID/SHA-256. La provenance cryptographique du corpus client n’est pas démontrée. | R25 |
| ASI06.6 | Empêcher la réingestion automatique comme source fiable | R | **R** | Contrôle explicite du cycle de réingestion des sorties d’agent à ajouter. | — |
| ASI06.7 | Quarantaine, reprise et revue des mémoires risquées | V | **V** | R13 refuse une écriture hostile avant persistance et vérifie le retour à la base saine ; des tests locaux couvrent quarantaine et snapshots. Pas de revue/reprise d’un magasin réel déjà contaminé. | R13, tests MemoryShield |
| ASI06.8 | Expiration des mémoires non vérifiées | R | **R** | Durée de vie et purge automatique de chaque entrée non vérifiée à implémenter. | — |
| ASI06.9 | Recherche conditionnée à la provenance et à la validation | R | **R** | R25 suit un chunk FTS préchargé mais ne conditionne pas une recherche sensible à provenance authentifiée et validité/TTL. La mesure reste à réaliser. | R25 |

<a id="asi07"></a>

### ASI07 — Communications interagents non sûres

| Repère interne | Mesure suivie | R14 | Relecture | Observation et limite | Repères de preuve |
| --- | --- | :---: | :---: | --- | --- |
| ASI07.1 | Canaux chiffrés et authentification mutuelle | P | **V** | Vraie connexion TLS de laboratoire : certificat client approuvé accepté, certificat absent ou autre AC refusés. Identités agent, rotation et PKI de déploiement restent ouvertes. | tests TLS |
| ASI07.2 | Intégrité du contenu et du contexte | P | **V** | R12/R14 : altération du ciphertext HPKE ou du contexte refusée, avec audit et corrélation Cyber sur le tir ciblé. P0-02 global reste INCONCLUSIVE. | R12, R14 |
| ASI07.3 | Antirejeu lié au contexte et au temps | P | **V** | R10–R12 : une seule acceptation du nonce concurrent, rejeu exact refusé et jeton authentique expiré après 3 604 s rejeté. Fenêtres de tâche et P0-02 global restent ouverts. | R10, R11, R12 |
| ASI07.4 | Refus des modes faibles et contrôle des capacités | P | **V** | R11/R12 refusent la preuve hybride incomplète et un mode HPKE dégradé ; le témoin complet est accepté. V limité aux modes testés, sans registre client exhaustif. | R11, R12 |
| ASI07.5 | Réduire les fuites par métadonnées de trafic | R | **R** | Padding et régulation des tailles/cadences de messages non implémentés. | — |
| ASI07.6 | Versions de protocole et capacités compatibles | P | **P** | Schémas stricts et domaine de signature versionné ; négociation de profils entre pairs à ajouter. | — |
| ASI07.7 | Découverte et routage authentifiés | P | **P** | Registre local sans inscription publique ; découverte fédérée non déployée. | — |
| ASI07.8 | Registres et fiches d’agents attestés | P | **P** | Clés publiques épinglées localement ; cartes d’agents signées et chaîne d’attestation à ajouter. | — |
| ASI07.9 | Contrats typés et audience explicite | P | **V** | Audience imposée par le serveur : champs client hors schéma refusés ; mauvais destinataire HPKE et message signé altéré rejetés. Interopérabilité entre piles tierces non éprouvée. | R12, tests A2A |

<a id="asi08"></a>

### ASI08 — Défaillances en cascade

| Repère interne | Mesure suivie | R14 | Relecture | Observation et limite | Repères de preuve |
| --- | --- | :---: | :---: | --- | --- |
| ASI08.1 | Conception tolérant l’indisponibilité des composants | P | **V** | R14 : audit saturé à zéro octet libre, refus fermé audit_unavailable et alerte Cyber ; reprise et chaîne vérifiées après restauration. Pannes distribuées non testées. | R14 |
| ASI08.2 | Isolation, segmentation et interfaces restreintes | P | **V** | R23 isole Acta via AppContainer/IPC et refuse un flux direct ciblé ; R35/R36B refusent à Cyber 18 ouvertures sur neuf secrets EAS. V borné aux chemins exercés. | R23, R35, R36B |
| ASI08.3 | Autorisations temporaires par appel sensible | R | **R** | Capacités outils à usage unique liées à la tâche à implémenter. | — |
| ASI08.4 | Politique indépendante du planificateur | V | **V** | P0-05 démontre l’indépendance du plan défensif ; R35 observe le vrai service Cyber sous LocalService pendant l’arrêt/redémarrage d’EAS. | R14, R35 |
| ASI08.5 | Contrôles avant propagation des résultats | P | **P** | Filtrage et décisions de revue ; autorisation de propagation métier à compléter. | — |
| ASI08.6 | Limites de débit et surveillance des anomalies | P | **P** | Tests locaux : 21e appel bloqué après quota de 20 et signal RUNAWAY_LOOP sur séquence répétée. Pas de reçu VM natif de ce débit/effet sur un agent réel. | tests locaux |
| ASI08.7 | Limites d’impact et mécanismes de coupure | P | **V** | P0-06 : Cyber met en quarantaine le canari Red enrôlé au même SHA et restaure l’état ; R45 arrête un parent et son enfant observés. Portée bornée à ces objets/PID. | R12, R45 |
| ASI08.8 | Suivi des dérives de comportement et de gouvernance | P | **P** | Moniteur de séquences ; baseline métier sur longue durée à établir. | — |
| ASI08.9 | Rejeu isolé des traces avant extension des politiques | R | **R** | Pipeline de validation des changements par rejeu des traces métier à mettre en place. | — |
| ASI08.10 | Traces signées et filiation des actions | P | **P** | Reçus EAS corrélés ; R40 rapproche trois mutations Store Acta de sept décisions EAS. Le ledger EAS ne certifie pas toute la SQLite Acta ni toutes les propagations. | R40 |

<a id="asi09"></a>

### ASI09 — Manipulation de la confiance humaine

| Repère interne | Mesure suivie | R14 | Relecture | Observation et limite | Repères de preuve |
| --- | --- | :---: | :---: | --- | --- |
| ASI09.1 | Approbations explicites des opérations sensibles | P | **P** | TestClient local : confirmation exacte et opérateur simulé exigés pour une levée de confinement. Aucun opérateur humain ni effet natif VM sur ce parcours. | tests locaux |
| ASI09.2 | Journaux résistants à l’altération | V | **V** | P0-09 R14 : refus fermé à 0 octet libre, alerte Cyber, chaîne continue et quatre mutations détectées sur copies isolées. La preuve reste bornée à ces essais. | R14 |
| ASI09.3 | Détection d’expositions et d’actions sensibles | P | **P** | Filtres et moniteur ; couverture de toutes les conversations/connecteurs à compléter. | — |
| ASI09.4 | Signalement d’interactions suspectes par l’utilisateur | R | **R** | Parcours de signalement utilisateur avec gel/revue à implémenter. | — |
| ASI09.5 | Confiance adaptée au risque et formation | P | **P** | Décisions par risque présentes ; indices visuels et programme de formation à établir. | — |
| ASI09.6 | Provenance vérifiable et blocage des actions hors portée | P | **P** | Contrôles de capacités et preuve d’action renforcés par les campagnes R13/R14 ; provenance de toute recommandation reste à ajouter. | R13, R14 |
| ASI09.7 | Séparer aperçu et effet | P | **P** | TestClient local : GET d’aperçu sans effet, POST authentifié lié au hash exact avec changement d’état. Aucun parcours utilisateur natif VM qualifié. | tests locaux |
| ASI09.8 | Ergonomie de sécurité et évaluation des opérateurs | O | **O** | Parcours opérateur, repères de risque et évaluation humaine à construire avec l’exploitant. | — |
| ASI09.9 | Détection des écarts au parcours approuvé | P | **P** | Séquences surveillées ; workflows métier approuvés et déviations à formaliser. | — |

<a id="asi10"></a>

### ASI10 — Agents incontrôlés

| Repère interne | Mesure suivie | R14 | Relecture | Observation et limite | Repères de preuve |
| --- | --- | :---: | :---: | --- | --- |
| ASI10.1 | Gouvernance et traces des interactions/actions | P | **V** | R13 : vraies routes mémoire et code de Bonsaï, refus avant effet et traces corrélées ; R40 ajoute un tour Acta et ses décisions EAS. V sur ces interactions raccordées. | R13, R40 |
| ASI10.2 | Zones de confiance et isolation restrictive | P | **V** | R23 observe le service Acta, son shim et un enfant confinés avec refus ciblés ; R43/R44 observent des refus sous profil EAS signé. R48 confirme des accès fichier permis et refusés sur la lignée R42/R43 après pose des ACL par l'installateur de laboratoire corrigé R46. D'autres agents et chemins restent non qualifiés. | R23, R43, R44, R48 |
| ASI10.3 | Surveillance des anomalies et de la collusion | P | **P** | Séquences EAS et Cyber autonome prouvés sous panne/charge ; collusion multi-agent réelle non démontrée. | — |
| ASI10.4 | Arrêt, révocation et quarantaine rapide | P | **V** | P0-06 démontre la quarantaine native ; R45 : /stop EAS puis disparition vérifiée d’un parent et son enfant. Job exact et autres voies de l’agent restent INCONCLUSIVE. | R12, R45 |
| ASI10.5 | Attestation d’identité et manifeste comportemental signé | P | **P** | Authentification A2A hybride ; manifeste signé des objectifs/outils de chaque agent à ajouter. | — |
| ASI10.6 | Attestation périodique et protection des clés | P | **P** | Cyber tourne sous LocalService et se voit refuser l’ouverture directe de secrets EAS R35/R36B. Handles/copies indirects et HSM/KMS non qualifiés. | R35, R36B |
| ASI10.7 | Réintégration depuis une base de confiance | P | **P** | Reboot/reprise P0-10 et restaurations R13/R14 vérifiés ; réattestation complète d’un agent avant réintégration reste à formaliser. | R13, R14 |

## Limites transversales à conserver

- La médiation applicative protège les actions effectivement raccordées. Le mode géré ajoute une frontière OS aux processus lancés sous profil signé ; le confinement complet d'un agent tiers et de tous ses chemins directs reste à qualifier.
- Les résultats de laboratoire Windows ne sont pas automatiquement transposables au port Linux ou à une installation client.
- Les refus et vérifications du ledger cités en ASI08.1 et ASI09.2 couvrent les pannes et altérations observées ; ils ne démontrent pas tous les états possibles après une faute d'écriture de l'ancre ou une panne physique du support.
- Les contrôles de mémoire d'Acta n'étendent pas la portée de son ledger à tous les agents. Les trois portes P0 inconclusives conservent ce verdict dans leur protocole propre.

**Références :** [OWASP Agentic Top 10 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) · [architecture EAS](architecture.md) · [résultats expurgés](evidence.md). Les justificatifs internes détaillés sont consultables lors d'une évaluation accompagnée, après revue de divulgation.
