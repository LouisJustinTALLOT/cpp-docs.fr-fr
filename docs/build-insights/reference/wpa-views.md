---
title: 'Référence: Vues d’analyseur de performance Windows'
description: Référence pour les vues build Insights disponibles dans Windows Performance Analyzer.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b54b1b76d83b77ec7b8d8d3309d81ed9eb2db2d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323236"
---
# <a name="reference-windows-performance-analyzer-views"></a>Référence: Vues d’analyseur de performance Windows

::: moniker range="<=vs-2017"

Les outils build Insights sont disponibles dans Visual Studio 2019. Pour voir la documentation de cette version, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range="vs-2019"

Cet article fournit des détails sur chacune des vues build Insights disponibles dans Windows Performance Analyzer (WPA). Utilisez cette page pour trouver :

- descriptions de colonnes de données; Et
- préréglages disponibles pour chaque vue, y compris leur utilisation prévue et le mode de visualisation préféré.

Si vous êtes nouveau dans WPA, nous vous recommandons de vous familiariser d’abord avec les [bases de WPA pour les aperçus build .](/cpp/build-insights/tutorials/wpa-basics)

## <a name="build-explorer"></a>Build Explorer

La vue Build Explorer est utilisée pour :

- diagnostiquer les questions de parallélisme,
- déterminer si votre temps de construction est dominé par l’analyse, la génération de code ou le lien, et
- identifier les goulots d’étranglement et les activités de construction exceptionnellement longues.

### <a name="build-explorer-view-data-columns"></a>Construire Explorer afficher des colonnes de données

| Nom de la colonne | Description |
|-|-|
| BuildTimelineDescription | Une description textuelle de la chronologie de l’activité actuelle ou de la propriété se produit sur. |
| BuildTimelineId BuildTimelineId          | Un identifiant à base nulle pour le calendrier de l’activité actuelle ou de la propriété se produit sur. |
| Composant                | Le composant étant compilé ou lié lorsque l’événement actuel a été émis. La valeur de cette colonne est * \<Invocation X Info\> * lorsqu’aucun composant n’est associé à cet événement. X est un identifiant numérique unique pour l’invocation exécutée au moment de l’expiration de l’événement. Cet identifiant est le même que celui de la colonne InvocationId pour cet événement. |
| Count                    | Nombre d’activités ou de propriétés représentées par cette série de données. Cette valeur est toujours 1, et n’est utile que dans les scénarios d’agrégation lorsque plusieurs lignes sont regroupées. |
| ExclusifCPUTime         | La quantité de temps de processeur en millisecondes utilisées par cette activité. Le temps passé dans les activités des enfants n’est pas inclus dans ce montant. |
| ExclusiveDuration        | La durée de la milliseconde de l’activité. La durée des activités des enfants n’est pas incluse dans ce montant. |
| InclusiveCPUTime (en)         | La quantité de temps de processeur en millisecondes utilisées par cette activité et toutes les activités des enfants. |
| InclusiveDuration        | La durée de la milliseconde de cette activité, y compris toutes les activités des enfants. |
| InvocationDescription    | Une description textuelle de l’invocation de cet événement s’est produite dedans. La description comprend si c’était *cl.exe* ou *link.exe*, et un identificateur d’invocation numérique unique. Le cas échéant, il comprend le chemin complet vers le composant compilé ou lié pendant l’invocation. Pour les invocations qui ne construisent aucun composant, ou pour ceux qui construisent plusieurs composants, le chemin est vide. L’identifiant d’invocation est le même que celui de la colonne InvocationId. |
| InvocationId             | Un identificateur numérique unique pour l’invocation de cet événement s’est produit. |
| Nom                     | Le nom de l’activité ou de la propriété représentée par cet événement. |
| Temps                     | Un timestamp qui identifie quand l’événement s’est produit. |
| Outil                     | L’outil exécutant lorsque cet événement s’est produit. La valeur de cette colonne est soit CL ou Link. |
| Type                     | Le type de l’événement actuel. Cette valeur est soit l’activité ou la propriété. |
| Value                    | Si l’événement actuel est une propriété, cette colonne contient sa valeur. Cette colonne est laissée vide lorsque l’événement actuel est une activité. |

### <a name="build-explorer-view-presets"></a>Construire Des préréglages de vue Explorer

| Nom Prédéfinis           | Mode vue préférée | Utilisation |
|-----------------------|---------------------|------------|
| Statistiques d’activité   | Graphique / Tableau       | Utilisez ce préréglage pour afficher les statistiques agrégées pour toutes les activités de Build Explorer. En mode table, indiquez en un coup d’œil si votre build est dominée par l’analyse, la génération de code ou le lien. Les durées agrégées pour chaque activité sont triées dans l’ordre décroissant. Percer en élargissant le nœud supérieur pour trouver facilement quelles invocations prennent le plus de temps pour ces activités de haut niveau. Si vous le souhaitez, vous pouvez ajuster les paramètres WPA pour afficher des moyennes ou d’autres types d’agrégations. En mode graphique, voyez quand chaque activité est active pendant votre version. |
| Invocations           | Graph               | Faites défiler vers le bas une liste d’invocations dans la vue graphique triée à l’heure de début. Vous pouvez l’utiliser avec la vue CPU (Sampled) pour trouver des invocations qui s’alignent avec de faibles zones d’utilisation du processeur. Détecter les problèmes de parallélisme. |
| Propriétés d’invocation | Table de charge de travail               | Trouvez rapidement des informations clés sur une invocation donnée de compilateur ou de lien. Déterminez sa version, son répertoire de travail ou la ligne de commande complète utilisée pour l’invoquer. |
| Chronologies             | Graph               | Voyez un graphique à barres de la façon dont votre build a été parallélisé. Identifiez les questions de parallélisme et les goulots d’étranglement en un coup d’œil. Configurez WPA pour attribuer des significations différentes aux barres en fonction de vos besoins. Choisissez des descriptions d’invocation comme dernière colonne groupée pour afficher un graphique à barres codé en couleur de toutes vos invocations. Il vous aide à identifier rapidement les coupables qui prennent beaucoup de temps. Ensuite, zoomez et choisissez le nom d’activité comme dernière colonne groupée pour voir les parties les plus longues. |

## <a name="files"></a>Fichiers

La vue Fichiers est utilisée pour :

- déterminer quels en-têtes sont inclus le plus souvent, et
- vous aider à décider quoi inclure dans un en-tête pré-compilé (PCH).

### <a name="files-view-data-columns"></a>Les fichiers affichent les colonnes de données

| Nom de la colonne              | Description |
|--------------------------|-------------|
| ActivityName             | L’activité en cours lors de l’événement de ce fichier a été émise. Actuellement, cette valeur est toujours *Parsing*. |
| BuildTimelineDescription | * |
| BuildTimelineId BuildTimelineId          | * |
| Composant                | * |
| Count                    | * |
| Profondeur                    | La position à base nulle dans l’arbre inclus dans lequel ce fichier est trouvé. Le comptage commence à la racine de l’arbre inclus. Une valeur de 0 correspond généralement à un fichier .c/.cpp. |
| ExclusiveDuration        | * |
| InclusBy               | La voie complète du fichier qui comprenait le fichier actuel. |
| InclusPath             | Le chemin complet du dossier actuel. |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | Un timetamp qui représente l’heure à laquelle l’événement de fichier actuel a été émis. |
| Outil                     | * |

\*La valeur de cette colonne est la même que dans la vue [Build Explorer.](#build-explorer-view-data-columns)

### <a name="files-view-presets"></a>Les fichiers affichent les préréglages

| Nom Prédéfinis | Mode vue préférée | Utilisation |
|-------------|---------------------|------------|
| Statistiques  | Table de charge de travail               | Voyez quels fichiers ont eu le temps d’analyse agrégé le plus élevé en regardant la liste dans l’ordre décroissant. Utilisez ces informations pour vous aider à restructurer vos en-têtes ou décider quoi inclure dans votre PCH. |

## <a name="functions"></a>Fonctions

La vue Functions est utilisée pour identifier les fonctions avec un temps de génération de code excessivement long.

### <a name="functions-view-data-columns"></a>Les fonctions affichent les colonnes de données

| Nom de la colonne              | Description |
|--------------------------|-------------|
| ActivityName             | L’activité en cours lors de cet événement de fonction a été émise. Actuellement, cette valeur est toujours *CodeGeneration*. |
| BuildTimelineDescription | * |
| BuildTimelineId BuildTimelineId          | * |
| Composant                | * |
| Count                    | * |
| Duration                 | La durée de l’activité de génération de code pour cette fonction. |
| FunctionName             | Le nom de la fonction en cours de génération de code. |
| InvocationId             | * |
| StartTime                | Un timestamp qui représente lorsque l’événement de fonction actuel a été émis. |
| Outil                     | * |

\*La valeur de cette colonne est la même que dans la vue [Build Explorer.](#build-explorer-view-data-columns)

### <a name="functions-view-presets"></a>Fonctions voir presets

| Nom Prédéfinis | Mode vue préférée | Utilisation |
|-------------|---------------------|------------|
| Statistiques  | Table de charge de travail               | Voyez quelles fonctions avaient le temps de génération de code agrégé le plus élevé en regardant la liste dans l’ordre décroissant. Ils peuvent suggérer où votre code surutilise le mot clé **__forceinline,** ou que certaines fonctions peuvent être trop grandes. |
| Chronologies   | Graph               | Regardez ce graphique à barres pour apprendre l’emplacement et la durée des fonctions qui prennent le plus de temps à générer. Voir s’ils s’alignent avec les goulots d’étranglement dans la vue Build Explorer. S’ils le font, prenez les mesures appropriées pour réduire leur temps de génération de code et bénéficier à vos temps de construction. |

## <a name="see-also"></a>Voir aussi

[Commencez avec les aperçus de construction de CMD](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Référence: commandes de vcperf](vcperf-commands.md)\
[Tutorial: Windows Performance Analyzer basics](/cpp/build-insights/tutorials/wpa-basics)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
