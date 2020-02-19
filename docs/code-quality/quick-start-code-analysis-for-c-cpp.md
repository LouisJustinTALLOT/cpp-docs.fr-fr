---
title: 'Démarrage rapide : analyse du code pour C/C++'
description: Exécutez une analyse statique C++ sur le code dans Visual Studio pour détecter les problèmes de codage courants et les défauts.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.openlocfilehash: 5ee8f702ddf489732f664ae73eed75b18dc46e86
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77418780"
---
# <a name="quickstart-code-analysis-for-cc"></a>Démarrage rapide : analyse du code pour C/C++

Vous pouvez améliorer la qualité de votre application en exécutant l'analyse de code de manière régulière sur le code C ou C++. Cela peut vous aider à rechercher les problèmes courants, les violations d'une bonne pratique de programmation ou les défauts difficiles à détecter à travers des tests. Les avertissements de l'analyse du code diffèrent des erreurs et des avertissements du compilateur, car l'analyse du code recherche des modèles de code spécifiques qui sont valides, mais qui peuvent créer des problèmes pour vous ou d'autres utilisateurs de votre code.

## <a name="configure-rule-sets-for-a-project"></a>Configurer des ensembles de règles pour un projet

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nom du projet, puis choisissez **Propriétés**.

1. Si vous le souhaitez, dans les listes **configuration** et **plateforme** , choisissez la configuration de build et la plateforme cible.

1. Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, activez la case à cocher **activer l’analyse du code sur la build** . Vous pouvez également exécuter l’analyse du code manuellement en ouvrant le menu **analyser** , puis en sélectionnant **exécuter l’analyse du code sur** *ProjectName* ou **exécuter l’analyse du code sur le fichier**.

1. Choisissez l' [ensemble de règles](using-rule-sets-to-specify-the-cpp-rules-to-run.md) que vous souhaitez utiliser ou créez un [ensemble de règles personnalisé](using-rule-sets-to-specify-the-cpp-rules-to-run.md#to-create-a-rule-set-in-a-text-editor). Si vous utilisez LLVM/Clang-CL, consultez [utilisation de Clang-Tidy dans Visual Studio](../code-quality/clang-tidy.md) pour configurer les options d’analyse Clang-Tidy.

### <a name="standard-cc-rule-sets"></a>Ensembles de règles standard C/C++

Visual Studio inclut deux ensembles de règles standard pour le code natif :

|Ensemble de règles|Description|
|--------------|-----------------|
|Règles minimales recommandées par Microsoft pour les projets natifs|Cet ensemble de règles couvre les problèmes les plus critiques rencontrés dans votre code natif, notamment les failles de sécurité potentielles et les blocages d'application. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.|
|Règles recommandées natives Microsoft|Cet ensemble de règles couvre une large gamme de problèmes. Il inclut toutes les règles dans l'ensemble Règles minimales recommandées par Microsoft pour les projets natifs.|

## <a name="run-code-analysis"></a>Exécuter l'analyse du code

Sur la page analyse du code de la page de propriétés du projet, vous pouvez configurer l’analyse du code pour qu’elle s’exécute chaque fois que vous générez votre projet. Vous pouvez également exécuter l'analyse du code manuellement.

Pour exécuter l'analyse du code sur une solution :

- Dans le menu **générer** , choisissez **exécuter l’analyse du code sur la solution**.

Pour exécuter l'analyse du code sur un projet :

1. Dans le Explorateur de solutions, sélectionnez le nom du projet.

1. Dans le menu **générer** , choisissez **exécuter l’analyse du code sur le nom du** *projet*.

Pour exécuter l’analyse du code sur un fichier :

1. Dans le Explorateur de solutions, sélectionnez le nom du fichier.

1. Dans le menu **générer** , choisissez **exécuter l’analyse du code sur le fichier** ou appuyez sur **Ctrl + Maj + Alt + F7**.

   Le projet ou la solution est compilé et l'analyse du code est exécutée. Les résultats s’affichent dans la Liste d’erreurs.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analyser et résoudre les avertissements d'analyse du code

Pour analyser un avertissement spécifique, choisissez le titre de l’avertissement dans la Liste d’erreurs. L'avertissement se développe pour afficher des informations supplémentaires sur le problème. Dans la mesure du possible, l'analyse du code affiche les numéros de ligne et la logique d'analyse qui a conduit à l'avertissement. Pour plus d’informations sur l’avertissement, y compris les solutions possibles pour le problème, choisissez l’ID d’avertissement pour afficher la rubrique d’aide en ligne correspondante.

Lorsque vous sélectionnez un avertissement, la ligne de code à l’origine de l’avertissement est mise en surbrillance dans l’éditeur de code Visual Studio.

Après avoir identifié le problème, vous pouvez le résoudre dans votre code. Ensuite, réexécutez l’analyse du code pour vous assurer que l’avertissement n’apparaît plus dans la Liste d’erreurs et que votre correctif n’a pas généré de nouveaux avertissements.

## <a name="suppress-code-analysis-warnings"></a>Supprimer les avertissements d’analyse du code

Vous pouvez décider, dans certaines situations, de ne pas corriger un avertissement de l'analyse du code. Vous pouvez décider que la résolution de l'avertissement requiert un recodage trop important par rapport à la probabilité que le problème se produise dans une implémentation réelle de votre code. Vous pouvez également estimer que l'analyse utilisée dans l'avertissement est inadéquate pour le contexte particulier. Vous pouvez supprimer des avertissements individuels afin qu’ils n’apparaissent plus dans la Liste d’erreurs.

### <a name="to-suppress-a-warning"></a>Pour supprimer un avertissement

1. Si les informations détaillées ne sont pas affichées, choisissez le titre de l'avertissement pour le développer.

1. Choisissez le lien **Actions** au bas de l’avertissement.

1. Choisissez **supprimer le message** , puis sélectionnez **dans la source**.

   La suppression d’un message insère `#pragma warning (disable:[warning ID])` qui supprime l’avertissement pour la ligne de code.

## <a name="create-work-items-for-code-analysis-warnings"></a>Créer des éléments de travail pour les avertissements d’analyse du code

Vous pouvez utiliser la fonctionnalité de suivi des éléments de travail pour enregistrer les bogues à partir de Visual Studio. Pour utiliser cette fonctionnalité, vous devez vous connecter à une instance de Team Foundation Server.

### <a name="to-create-a-work-item-for-one-or-more-cc-code-warnings"></a>Pour créer un élément de travail pour un ou plusieurs avertissements de code C/C++

1. Dans le Liste d’erreurs, développez et sélectionnez les avertissements.

1. Dans le menu contextuel des avertissements, choisissez **créer un élément de travail**, puis choisissez le type d’élément de travail.

1. Visual Studio crée un élément de travail unique pour les avertissements sélectionnés et affiche l’élément de travail dans une fenêtre de document de l’IDE.

1. Ajoutez des informations supplémentaires, puis choisissez **enregistrer l’élément de travail**.

## <a name="search-and-filter-code-analysis-results"></a>Rechercher et filtrer les résultats de l’analyse du code

Vous pouvez effectuer une recherche dans de longues listes de messages d'avertissement et filtrer les avertissements dans les solutions à projets multiples.

- **Pour filtrer les avertissements par titre ou ID d’avertissement**: entrez le mot clé dans la zone de recherche.

- **Pour filtrer les avertissements par gravité**: par défaut, les messages d’analyse du code sont affectés d’un niveau de gravité **Avertissement**. Vous pouvez affecter la gravité d’un ou plusieurs messages en tant qu' **erreur** dans un ensemble de règles personnalisé. Dans la colonne **gravité** de la **liste d’erreurs**, cliquez sur la flèche déroulante, puis sur l’icône de filtre. Choisissez **Avertissement** ou **erreur** pour afficher uniquement les messages qui sont affectés à la gravité respective. Choisissez **Sélectionner tout** pour afficher tous les messages.

## <a name="see-also"></a>Voir aussi

- [Analyse du code pour C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
