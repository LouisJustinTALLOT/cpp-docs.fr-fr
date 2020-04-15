---
title: 'Démarrage rapide : analyse du code pour C/C++'
description: Exécutez l’analyse statique sur le code CMD dans Visual Studio pour détecter les problèmes et les défauts de codage courants.
ms.date: 04/08/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis, C/C++
ms.openlocfilehash: 43866564915ac84d227ccbf347280efe59e33351
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370574"
---
# <a name="quickstart-code-analysis-for-cc"></a>Démarrage rapide : analyse du code pour C/C++

Vous pouvez améliorer la qualité de votre application en exécutant l'analyse de code de manière régulière sur le code C ou C++. L’analyse du code peut vous aider à trouver des problèmes communs et des violations des bonnes pratiques de programmation. Et, il trouve des défauts qui sont difficiles à découvrir par le biais de tests. Ses avertissements diffèrent des erreurs et des avertissements des compilateurs : il recherche des modèles de code spécifiques qui sont connus pour causer des problèmes. C’est-à-dire, code qui est valide, mais pourrait encore créer des problèmes, que ce soit pour vous ou pour d’autres personnes qui utilisent votre code.

## <a name="configure-rule-sets-for-a-project"></a>Configurer des ensembles de règles pour un projet

1. Dans **Solution Explorer**, ouvrez le menu raccourci pour le nom du projet, puis choisissez **Propriétés**.

1. Optionnellement, dans les listes **Configuration** et **Plate-forme,** choisissez la configuration de construction et la plate-forme cible.

1. Pour exécuter l’analyse de code chaque fois que le projet est construit à l’aide de la configuration sélectionnée, sélectionnez **l’analyse de code active sur la** case à cocher Build. Vous pouvez également exécuter l’analyse de code manuellement en ouvrant le menu **Analyze,** puis en choisissant **l’analyse de code d’exécution sur** *ProjectName* ou **l’analyse de code d’exécution sur le fichier**.

1. Choisissez [l’ensemble de règles](using-rule-sets-to-specify-the-cpp-rules-to-run.md) que vous souhaitez utiliser ou créer un [ensemble de règles personnalisées](using-rule-sets-to-specify-the-cpp-rules-to-run.md#to-create-a-rule-set-in-a-text-editor). Si vous utilisez LLVM/clang-cl, voir [Utiliser Clang-Tidy dans Visual Studio](../code-quality/clang-tidy.md) pour configurer les options d’analyse Clang-Tidy.

### <a name="standard-cc-rule-sets"></a>Ensembles standard de règles C/CM

Visual Studio comprend ces ensembles standard de règles pour le code natif :

| Ensemble de règles | Description |
|--|--|
| **Règles d’arithmétique de vérification de base de CMD** | Ces règles appliquent les contrôles liés aux [opérations arithmétiques des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements)de C. |
| **Règles sur les limites de contrôle de base de CMD** | Ces règles appliquent le [profil Bounds des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)de C. |
| **Règles de classe de vérification de base de CMD** | Ces règles appliquent les contrôles liés aux [classes des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-classes-and-class-hierarchies)de C. |
| **Règles de concurrence de vérification de base de CMD** | Ces règles appliquent les contrôles liés à [la concurrence des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cpcon-concurrency)de C. . |
| **Règles de la const de vérification de base de CMD** | Ces règles appliquent [les vérifications liées à la const des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)de C. |
| **Règles de déclaration de vérification de base de CMD** | Ces règles appliquent les contrôles liés aux [déclarations des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i-interfaces)de la C. . |
| **Règles de cœur d’enum** | Ces règles appliquent [les contrôles liés à l’enum à partir des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-enum)de C. |
| **Règles expérimentales de vérification de base de CMD** | Ces règles recueillent des contrôles expérimentaux. Finalement, nous nous attendons à ce que ces contrôles soient transférés à d’autres règles ou supprimés complètement. |
| **Règles de fonction de contrôle de base de CMD** | Ces règles appliquent les contrôles liés aux [fonctions des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f-functions)de C. |
| **Règles GSL de CMD Core Check** | Ces règles appliquent les contrôles liés à la [Bibliothèque de soutien aux lignes directrices des Lignes directrices](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-gsl)de base . |
| **Règles à vie de C- Core Check** | Ces règles appliquent le [profil à vie des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prolifetime-lifetime-safety-profile)de C. |
| **Règles de pointeur de propriétaire de vérification de base de CMD** | Ces règles appliquent les contrôles de gestion des ressources liés au [propriétaire&lt;T&gt; des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)de C. |
| **Règles de pointeur brut de vérification de base de CMD** | Ces règles appliquent les contrôles de gestion des ressources liés aux [pointeurs bruts des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)de C. |
| **Règles de vérification de base de CMD** | Ces règles appliquent un sous-ensemble des contrôles des [Lignes directrices](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-core-guidelines)de base de C. Utilisez ce jeu de règles pour inclure toutes les règles de vérification de base de CMD, à l’exception des règles Enum et Experimental. |
| **Règles de pointeur partagé de CMD Core Check** | Ces règles appliquent les contrôles de gestion des ressources liés aux [types avec la sémantique des pointeurs partagés des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)de C. |
| **Règles st.L.C. Core Check** | Ces règles appliquent les contrôles liés à la [Bibliothèque de gabarit standard (TSL) de la Bibliothèque de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-stdlib)de C. |
| **Règles de style de contrôle de base de CMD** | Ces règles appliquent les contrôles liés à l’utilisation des [expressions et des déclarations des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements)de C. |
| **Règles de type de vérification de base de CMD** | Ces règles appliquent le [profil type des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)de C. |
| **Règles de pointeur unique de CMD Core Check** | Ces règles appliquent les contrôles de gestion des ressources liés aux types avec [une sémantique de pointage unique des Lignes directrices de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)de C. |
| **Règles de vérification de la concordance** | Ces règles appliquent un ensemble de contrôles de modèle de concurrence Win32 dans C. |
| **Règles de concurrence** | Ajoute des règles d’accord des lignes directrices de base de CMD aux règles de **vérification de la concordance**. |
| **Règles minimales natives Microsoft** | Ces règles mettent l’accent sur les problèmes les plus critiques de votre code natif, y compris les failles de sécurité potentielles et les accidents d’application. Nous vous recommandons d’inclure cette règle définie dans n’importe quel ensemble de règles personnalisées que vous créez pour vos projets autochtones. |
| **Règles recommandées natives Microsoft** | Ces règles mettent l’accent sur les problèmes les plus critiques et les plus courants de votre code natif. Ces problèmes comprennent les failles de sécurité potentielles et les accidents d’application. Nous vous recommandons d’inclure cette règle définie dans n’importe quel ensemble de règles personnalisées que vous créez pour vos projets autochtones. Ce jeu de règles est conçu pour fonctionner avec Visual Studio Professional édition et plus élevé. Il inclut toutes les règles dans **Microsoft Native Minimum Rules**. |

Visual Studio inclut ces ensembles standard de règles pour le code géré :

| Ensemble de règles | Description |
|--|--|
| **Règles microsoft de correction de base** | Ces règles mettent l’accent sur les erreurs de logique et les erreurs courantes commises dans l’utilisation des API-cadres. Inclure cette règle qui devrait s’étendre sur la liste des avertissements signalés par les règles minimales recommandées. |
| **Règles de ligne directrice microsoft de conception de base** | Ces règles mettent l’accent sur l’application des meilleures pratiques pour rendre votre code facile à comprendre et à utiliser. Inclure cette règle définie si votre projet inclut le code de bibliothèque ou si vous souhaitez appliquer les meilleures pratiques pour un code facilement maintenable. |
| **Règles microsoft de correction étendue** | Ces règles s’étendent sur les règles de base de la justesse afin de maximiser la logique et les erreurs d’utilisation des cadres signalés. L’accent est mis sur des scénarios spécifiques tels que l’interop COM et les applications mobiles. Envisagez d’inclure cette règle si l’un de ces scénarios s’applique à votre projet ou de trouver des problèmes supplémentaires dans votre projet. |
| **Règles de ligne directrice de conception étendue de Microsoft** | Ces règles s’étendent sur les règles de base de la conception pour maximiser les problèmes signalés d’utilisabilité et de maintenance. L’accent est mis sur les directives de nommage. Envisagez d’inclure cette règle définie si votre projet inclut le code de bibliothèque ou si vous souhaitez appliquer les normes les plus élevées pour écrire du code maintenable. |
| **Règles de mondialisation Microsoft** | Ces règles mettent l’accent sur les problèmes qui empêchent les données de votre application d’afficher correctement lorsqu’elles sont utilisées dans différentes langues, lieux et cultures. Inclure cette règle définie si votre application est localisée et/ou mondialisée. |
| **Règles minimales gérées par Microsoft** | Ces règles mettent l’accent sur les problèmes les plus critiques de votre code pour lesquels l’analyse de code est la plus précise.  Ces règles sont peu nombreuses et elles ne sont destinées qu’à être exécutées dans des éditions limitées de Visual Studio.  Utilisez MinimumRecommendedRules.ruleset avec d’autres éditions Visual Studio. |
| **Microsoft a géré les règles recommandées** | Ces règles se concentrent sur les problèmes les plus critiques de votre code. Ces problèmes comprennent des failles de sécurité potentielles, des plantages d’application, et d’autres erreurs importantes de logique et de conception. Nous vous recommandons d’inclure cette règle définie dans n’importe quel ensemble de règles personnalisées que vous créez pour vos projets. |
| **Règles minimales Microsoft Mixed (CMD/CLR)** | Ces règles mettent l’accent sur les problèmes les plus critiques de vos projets CMD qui prennent en charge le temps de course de langue commune. Ces problèmes comprennent des failles de sécurité potentielles, des plantages d’application, et d’autres erreurs importantes de logique et de conception. Nous vous recommandons d’inclure cette règle définie dans n’importe quel ensemble de règles personnalisées que vous créez pour vos projets CMD qui prennent en charge le temps d’exécution de la langue commune. |
| **Règles microsoft Mixtes (CD/CLR) recommandées** | Ces règles mettent l’accent sur les problèmes les plus courants et les plus critiques de vos projets CMD qui prennent en charge le temps de course à la langue commune. Ces problèmes comprennent des failles de sécurité potentielles, des plantages d’application, et d’autres erreurs importantes de logique et de conception. Ce jeu de règles est conçu pour une utilisation dans l’édition Visual Studio Professional et plus élevé. |
| **Règles de sécurité Microsoft** | Cet ensemble de règles contient toutes les règles de sécurité Microsoft. Inclure cette règle visant à maximiser le nombre de problèmes de sécurité potentiels qui sont signalés. |

Pour inclure toutes les règles :

| Ensemble de règles | Description |
|--|--|
| **Microsoft Toutes les règles** | Cet ensemble de règles contient toutes les règles. L’exécution de cet ensemble de règles peut entraîner la mise en œt d’un grand nombre d’avertissements. Utilisez cet ensemble de règles pour obtenir une image complète de toutes les questions de votre code. Il peut vous aider à décider lequel des ensembles de règles les plus ciblés sont les plus appropriés pour exécuter pour vos projets. |

## <a name="run-code-analysis"></a>Exécuter l'analyse du code

Sur la page **d’analyse** de code du dialogue Project Properties, vous pouvez configurer l’analyse de code pour exécuter chaque fois que vous construisez votre projet. Vous pouvez également exécuter l'analyse du code manuellement.

Pour exécuter l'analyse du code sur une solution :

- Dans le menu **Build,** choisissez **l’analyse du code d’exécution sur la solution**.

Pour exécuter l'analyse du code sur un projet :

1. Dans la Solution Explorer, sélectionnez le nom du projet.

1. Dans le menu **Build,** choisissez **l’analyse du code d’exécution sur** *le nom du projet*.

Pour exécuter l’analyse de code sur un fichier :

1. Dans la Solution Explorer, sélectionnez le nom du fichier.

1. Dans le menu **Build,** choisissez **l’analyse de code d’exécution sur fichier** ou appuyez sur **Ctrl-Shift-Alt-F7**.

   Le projet ou la solution est compilé et l'analyse du code est exécutée. Les résultats apparaissent dans la fenêtre de la liste d’erreurs.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analyser et résoudre les avertissements d'analyse du code

La fenêtre Error List répertorie les avertissements d’analyse de code trouvés. Les résultats sont affichés dans un tableau. Si plus d’informations sont disponibles sur un avertissement particulier, la première colonne contient un contrôle d’expansion. Choisissez-le pour étendre l’affichage pour plus d’informations sur le problème. Dans la mesure du possible, l'analyse du code affiche les numéros de ligne et la logique d'analyse qui a conduit à l'avertissement.

Pour obtenir des informations détaillées sur l’avertissement, y compris des solutions possibles au problème, choisissez l’identifiant d’avertissement dans la colonne Code pour afficher son article d’aide en ligne correspondant.

Double-cliquez sur un avertissement pour déplacer le curseur vers la ligne de code qui a causé l’avertissement dans l’éditeur de code Visual Studio. Ou, appuyez sur Entrez sur l’avertissement sélectionné.

Après avoir identifié le problème, vous pouvez le résoudre dans votre code. Ensuite, réexécutez l’analyse de code pour s’assurer que l’avertissement n’apparaît plus dans la liste d’erreurs.

## <a name="create-work-items-for-code-analysis-warnings"></a>Créer des éléments de travail pour les avertissements d’analyse de code

Vous pouvez utiliser la fonctionnalité de suivi des éléments de travail pour enregistrer les bogues à partir de Visual Studio. Pour utiliser cette fonctionnalité, vous devez vous connecter à une instance de Azure DevOps Server (anciennement, Team Foundation Server).

### <a name="to-create-a-work-item-for-one-or-more-cc-code-warnings"></a>Pour créer un élément de travail pour un ou plusieurs avertissements de code C/C++

1. Dans la liste d’erreurs, élargissez et sélectionnez les avertissements

1. Sur le menu raccourci pour les avertissements, choisissez **Créer l’élément de travail,** puis choisissez le type d’élément de travail.

1. Visual Studio crée un élément de travail unique pour les avertissements sélectionnés et affiche l’élément de travail dans une fenêtre de document de l’IDE.

1. Ajoutez des informations supplémentaires, puis choisissez **l’élément de travail Enregistrer**.

## <a name="search-and-filter-code-analysis-results"></a>Résultats d’analyse de code de recherche et de filtre

Vous pouvez effectuer une recherche dans de longues listes de messages d'avertissement, et vous pouvez filtrer les avertissements dans les solutions à projets multiples.

- **Pour filtrer les avertissements par titre ou identifiant d’avertissement**: Entrez le mot clé dans la boîte de liste d’erreurs de recherche.

- **Pour filtrer les avertissements par gravité**: Par défaut, les messages d’analyse de code sont attribués une sévérité d’avertissement . **Warning** Vous pouvez attribuer la sévérité d’un ou plusieurs messages comme **erreur** dans un ensemble de règles personnalisées. Sur la colonne **de gravité** de la **liste d’erreurs**, choisissez la flèche de chute, puis l’icône de filtre. Choisissez **Avertissement** ou **Erreur** pour afficher uniquement les messages qui sont attribués à la sévérité respective. Choisissez **Select All** pour afficher tous les messages.

## <a name="see-also"></a>Voir aussi

- [Analyse du code pour C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
