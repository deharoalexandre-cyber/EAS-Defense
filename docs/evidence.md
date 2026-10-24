# Qualifications : synthèse expurgée

[English](evidence.en.md) · [Accueil](../README.md)

Ce document résume des observations de laboratoire sans publier de reçus bruts, chemins de laboratoire, configuration de sécurité, règles internes ou modes opératoires offensifs. **Une qualification est attachée à sa version et à son périmètre.** Les résultats ci-dessous ne sont pas additionnables en un score global.

| Référence | Effet observé | Limite de la conclusion |
| --- | --- | --- |
| **R43 — Windows, clone de laboratoire** | Refus d’accès direct à un canari fichier depuis une sonde AppContainer ; canari inchangé après l’essai. | Refus ciblé, pas preuve du confinement de tous les accès fichier. |
| **R44 — Windows, clone de laboratoire** | Connexion ciblée refusée depuis le processus confiné ; contrôle positif de connectivité réalisé. | Ne démontre pas le refus de toutes les destinations et voies réseau ; l’attribution au composant Windows exact reste bornée. |
| **R45 — Windows, clone de laboratoire** | Un processus enfant conserve l’identité AppContainer ; son arrêt est vérifié lorsque EAS arrête le processus géré. | Ne valide pas le cycle de vie de tous les arbres de processus ni un agent tiers complet. |
| **R48 — Windows, clone de laboratoire** | Deux accès fichier autorisés et deux ouvertures refusées observés sur la lignée R42/R43 après pose des ACL par l’installateur de laboratoire corrigé R46, sans retouche manuelle de la zone autorisée durant R48. | Résultat dépendant des ACL et de la ressource testées ; ne constitue pas un rejeu de R45 ni une qualification de l’installateur commercial. |
| **P0-05 — R10** | Elyne Cyber est resté actif lorsque le service EAS a été arrêté. | Essai antérieur, non rejoué sur R45 ; pas une preuve d’indépendance complète des privilèges OS. |
| **Red R21B — clone Windows antérieur** | 19/19 jobs classés « défendus » ; 43/52 étapes défendues et 9 indéterminées. | Les 9 étapes ne sont pas des PASS. Cette campagne ne qualifie pas R45. |

Les tentatives initiales classées **INCONCLUSIVE** restent conservées comme telles ; les observations bornées ultérieures ne les changent pas rétroactivement en PASS. L’identification indépendante du Job EAS exact, l’attribution de certains refus d’initialisation Windows et le confinement intégral d’un agent tiers complet restent à qualifier.

La version **Windows R45** reste la référence d’évaluation technique accompagnée. Le port **Linux** poursuit sa qualification de laboratoire.

Les preuves détaillées peuvent être examinées dans le cadre d’une évaluation accompagnée, après revue de divulgation. [Contacter Elyne Corp](mailto:admin@elynecorp.fr?subject=Evaluation%20EAS%20Defense) · [Présentation publique](https://elynecorp.fr/eas-defense.html).
