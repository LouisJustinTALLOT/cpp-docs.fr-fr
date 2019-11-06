---
title: 'C++Build Insights : informations de référence sur les vues de l’analyseur de performances Windows'
description: Informations de C++ référence sur les vues de build Insights disponibles dans l’analyseur de performances Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e574e7ef4c1b4c5832785d69dbc90ba043cf996a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633090"
---
# <a name="c-build-insights-windows-performance-analyzer-views-reference"></a>C++Build Insights : informations de référence sur les vues de l’analyseur de performances Windows

::: moniker range="<=vs-2017"

Les C++ outils de génération Insights sont disponibles dans Visual Studio 2019. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

Cet article fournit des détails sur chacune des C++ vues de build Insights disponibles dans l’analyseur de performances Windows (WPA). Utilisez cette page pour rechercher :

- descriptions des colonnes de données ; les
- présélections disponibles pour chaque vue, y compris l’utilisation prévue et le mode d’affichage préféré.

Si vous débutez avec WPA, nous vous recommandons de commencer par vous familiariser avec les [principes de C++ base de l’activation de la norme WPA pour générer des Insights](wpa-basics.md).

## <a name="build-explorer"></a>Explorateur de builds

La vue Explorateur de builds permet d’effectuer les opérations suivantes :

- diagnostiquer les problèmes de parallélisme,
- Déterminez si votre temps de génération est dominé par l’analyse, la génération de code ou la liaison, et
- Identifiez les goulots d’étranglement et les activités de génération exceptionnellement longues.

### <a name="build-explorer-view-data-columns"></a>Afficher les colonnes de données de l’Explorateur de builds

| Nom de la colonne | Description |
|-|-|
| BuildTimelineDescription | Description textuelle de la chronologie sur laquelle se produit l’activité ou la propriété actuelle. |
| BuildTimelineId          | Identificateur de base zéro pour la chronologie dans laquelle l’activité ou la propriété actuelle se produit. |
| Composant                | Composant en cours de compilation ou lié lorsque l’événement actuel a été émis. La valeur de cette colonne est *\<l’appel de X Info\>* quand aucun composant n’est associé à cet événement. X est un identificateur numérique unique pour l’appel en cours d’exécution au moment de l’émission de l’événement. Cet identificateur est identique à celui de la colonne d’invocation de cet événement. |
| Count                    | Nombre d’activités ou de propriétés représentées par cette ligne de données. Cette valeur est toujours 1 et n’est utile que dans les scénarios d’agrégation lorsque plusieurs lignes sont regroupées. |
| ExclusiveCPUTime         | Temps processeur, en millisecondes, utilisé par cette activité. Le temps passé dans les activités enfants n’est pas inclus dans ce montant. |
| ExclusiveDuration        | Durée en millisecondes de l’activité. La durée des activités enfants n’est pas incluse dans ce montant. |
| InclusiveCPUTime         | Temps processeur, en millisecondes, utilisé par cette activité et toutes les activités enfants. |
| InclusiveDuration        | Durée en millisecondes de cette activité, y compris toutes les activités enfants. |
| InvocationDescription    | Description textuelle de l’appel que cet événement s’est produit dans. La description indique s’il s’agissait de *CL. exe* ou *Link. exe*, et d’un identificateur d’appel numérique unique. Le cas échéant, il comprend le chemin d’accès complet au composant compilé ou lié pendant l’appel. Pour les appels qui ne génèrent aucun composant, ou pour ceux qui génèrent plusieurs composants, le chemin d’accès est vide. L’identificateur d’appel est identique à celui de la colonne d’invocation. |
| InvocationId             | Identificateur numérique unique pour l’appel que cet événement s’est produit dans. |
| Name                     | Nom de l’activité ou de la propriété représentée par cet événement. |
| Heure                     | Horodateur qui identifie le moment où l’événement s’est produit. |
| Outil                     | L’outil s’exécutant lorsque cet événement s’est produit. La valeur de cette colonne est CL ou Link. |
| Tapez                     | Type de l’événement actuel. Cette valeur est une activité ou une propriété. |
| valeur                    | Si l’événement actuel est une propriété, cette colonne contient sa valeur. Cette colonne n’est pas renseignée lorsque l’événement actuel est une activité. |

### <a name="build-explorer-view-presets"></a>Vue d’ensemble de l’Explorateur de builds

| Nom de présélection           | Mode d’affichage par défaut | Utilisation |
|-----------------------|---------------------|------------|
| Statistiques d’activité   | Graphique/table       | Utilisez cette présélection pour afficher les statistiques agrégées pour toutes les activités de l’Explorateur de builds. En mode table, parlez-en un aperçu si votre Build est dominée par l’analyse, la génération de code ou l’éditeur de liens. Les durées agrégées de chaque activité sont triées dans l’ordre décroissant. Explorez en développant le nœud supérieur pour trouver facilement les appels qui prennent le plus de temps pour ces activités principales. Si vous le souhaitez, vous pouvez ajuster les paramètres WPA pour afficher des moyennes ou d’autres types d’agrégations. En mode graphique, consultez quand chaque activité est active pendant votre Build. |
| Appels           | Graphique               | Faites défiler la liste des appels dans la vue du graphique pour trier par heure de début. Vous pouvez l’utiliser avec la vue UC (échantillonnée) pour rechercher les appels qui s’alignent sur les zones d’utilisation du processeur faible. Détectez les problèmes de parallélisme. |
| Propriétés d’appel | Table               | Rechercher rapidement des informations clés sur un compilateur ou un appel de l’éditeur de liens donné. Déterminez sa version, le répertoire de travail ou la ligne de commande complète utilisée pour l’appeler. |
| chronologies             | Graphique               | Consultez un graphique à barres de la manière dont votre Build a été parallélisée. Identifiez les problèmes de parallélisme et les goulots d’étranglement en un clin d’œil. Configurez WPA pour affecter différentes significations aux barres en fonction de vos besoins. Choisissez descriptions d’appel comme dernière colonne regroupée pour afficher un graphique à barres codées en couleur de tous les appels. Cela vous permet d’identifier rapidement le temps que vous avez dû. Ensuite, effectuez un zoom avant et choisissez le nom de l’activité comme dernière colonne regroupée pour afficher les parties les plus longues. |

## <a name="files"></a>Fichiers

La vue fichiers permet d’effectuer les opérations suivantes :

- Déterminez les en-têtes qui sont inclus le plus souvent, et
- vous aider à choisir les éléments à inclure dans un en-tête précompilé (PCH).

### <a name="files-view-data-columns"></a>Colonnes de données d’affichage des fichiers

| Nom de la colonne              | Description |
|--------------------------|-------------|
| ActivityName             | Activité en cours lorsque cet événement de fichier a été émis. Actuellement, cette valeur est toujours en cours d' *analyse*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Composant                | * |
| Count                    | * |
| Profondeur                    | Position de base zéro dans l’arborescence include dans laquelle ce fichier est trouvé. Le comptage commence à la racine de l’arborescence d’inclusion. La valeur 0 correspond généralement à un fichier. c/. cpp. |
| ExclusiveDuration        | * |
| IncludedBy               | Chemin d’accès complet du fichier qui a inclus le fichier actif. |
| IncludedPath             | Chemin d’accès complet du fichier actif. |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | Horodateur qui représente l’heure à laquelle l’événement de fichier actuel a été émis. |
| Outil                     | * |

\* la valeur de cette colonne est identique à celle de la vue [Explorateur de builds](#build-explorer-view-data-columns) .

### <a name="files-view-presets"></a>Fichiers de vue prédéfinis

| Nom de présélection | Mode d’affichage par défaut | Utilisation |
|-------------|---------------------|------------|
| Statistiques  | Table               | Examinez les fichiers ayant le plus grand temps d’analyse agrégé en examinant la liste dans l’ordre décroissant. Utilisez ces informations pour vous aider à restructurer vos en-têtes ou à choisir les éléments à inclure dans votre PCH. |

## <a name="functions"></a>Fonctions

La vue Functions est utilisée pour identifier les fonctions avec une durée de génération de code excessivement longue.

### <a name="functions-view-data-columns"></a>Colonnes de données d’affichage des fonctions

| Nom de la colonne              | Description |
|--------------------------|-------------|
| ActivityName             | Activité en cours lorsque cet événement de fonction a été émis. Actuellement, cette valeur est toujours *CodeGeneration*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Composant                | * |
| Count                    | * |
| Duration                 | Durée de l’activité de génération de code pour cette fonction. |
| FunctionName             | Nom de la fonction qui subit la génération de code. |
| InvocationId             | * |
| StartTime                | Horodateur qui représente le moment où l’événement de fonction en cours a été émis. |
| Outil                     | * |

\* la valeur de cette colonne est identique à celle de la vue [Explorateur de builds](#build-explorer-view-data-columns) .

### <a name="functions-view-presets"></a>Présélections de vues de fonctions

| Nom de présélection | Mode d’affichage par défaut | Utilisation |
|-------------|---------------------|------------|
| Statistiques  | Table               | Consultez les fonctions qui ont eu le plus de temps de génération de code agrégé en examinant la liste dans l’ordre décroissant. Ils peuvent indiquer que votre code utilise le mot clé _ _ **forceinline** ou que certaines fonctions peuvent être trop volumineuses. |
| chronologies   | Graphique               | Examinez ce graphique à barres pour connaître l’emplacement et la durée des fonctions qui prennent le plus de temps à générer. Voyez s’ils s’alignent sur les goulots d’étranglement dans la vue de l’Explorateur de builds. Si c’est le cas, prenez les mesures appropriées pour réduire le temps de génération de code et tirer parti de vos temps de génération. |

## <a name="see-also"></a>Voir aussi

[Prise en main C++ de la\ de build Insights](get-started-with-cpp-build-insights.md)
informations de [référence sur vcperf. exe](vcperf-reference.md)\
[Notions de base de l’analyseur de performances Windows](wpa-basics.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
