---
title: Outils de l’IDE Visual Studio pour la mise à niveau du code C++
description: L’éditeur de code C++ et les outils d’analyse du code de Visual Studio vous aident à moderniser votre base de code C++.
ms.date: 11/13/2019
ms.topic: conceptual
ms.openlocfilehash: d6368445d16232ff968b7116b0f0313e97aa144c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503766"
---
# <a name="visual-studio-ide-tools-for-upgrading-c-code"></a>Outils de l’IDE Visual Studio pour la mise à niveau du code C++

Visual Studio vous aide à mettre à niveau le code C++ hérité avec les options du compilateur, les avertissements d’analyse du code et les fonctionnalités de l’éditeur telles que les correctifs rapides, les informations rapides et la barre de défilement améliorée. Le terme « code hérité » fait référence à l’une des catégories suivantes :

- Code précédemment autorisé par le compilateur Microsoft C++ (MSVC) mais jamais conforme à la norme C++.

   Pour mettre à niveau un ancien code MSVC non conforme, activez l’option du compilateur [/permissive-](../build/reference/permissive-standards-conformance.md) . Toutes les instances des utilisations non conformes sont soulignées par des tildes rouges dans l’éditeur de code. Les messages d’erreur dans la fenêtre de **liste d’erreurs** incluent une recommandation sur la manière de corriger l’erreur. Cliquez sur le code d’erreur pour accéder à sa page d’aide dans la documentation. Si la correction de toutes les erreurs à la fois est impossible, vous pouvez mettre à niveau le code non conforme par étapes en activant l’option **permissive** , en corrigeant certaines erreurs, puis en désactivant l’option. Le code est compilé avec les nouvelles améliorations, et vous pouvez revenir en arrière et corriger les problèmes restants ultérieurement. Consultez la page [/permissive-](../build/reference/permissive-standards-conformance.md) pour obtenir des exemples de code MSVC non conforme.

- Code qui était autorisé dans une version antérieure de la norme C++, mais qui a été déconseillé ou supprimé dans une version ultérieure.

   Pour effectuer une mise à niveau vers une norme de langage plus récente, définissez l’option [standard du langage C++](../build/reference/std-specify-language-standard-version.md) sur la norme souhaitée et corrigez toutes les erreurs de compilation déclenchées. En général, nous vous recommandons de définir la norme du langage sur [/std : c++ 17](../build/reference/std-specify-language-standard-version.md). Les erreurs déclenchées lors de la mise à niveau vers une version plus récente ne sont pas liées aux erreurs générées lors de l’utilisation de l’option **permissive** .

- Code conforme à toutes les versions de la norme, mais qui n’est plus considéré comme une meilleure pratique dans le C++ moderne.

   Pour identifier le code où les modifications sont recommandées, exécutez l' [analyse du code](../code-quality/code-analysis-for-c-cpp-overview.md).

## <a name="open-and-convert-a-legacy-project"></a>Ouvrir et convertir un projet hérité

Si votre projet hérité est basé sur une version antérieure de Visual Studio, vous pouvez l’ouvrir dans Visual Studio 2017 ou Visual Studio 2019. Visual Studio le convertit automatiquement en schéma de projet actuel avec la prise en charge de toutes les fonctionnalités les plus récentes du compilateur et de l’IDE.

![Mettre à niveau un projet](media/upgrade-dialog-v142.png "Mettre à niveau un projet")

Pour plus d’informations, consultez [mettre à niveau des projets C++ à partir de versions antérieures de Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

## <a name="search-the-code-base"></a>Rechercher dans la base de code

La mise à niveau d’une base de code implique souvent la recherche dans plusieurs fichiers. Pour rechercher des éléments dans votre base de code, appuyez sur **Ctrl + T** pour afficher la zone de recherche **atteindre tout** .

![Atteindre tout](media/go-to-all.png "Atteindre tout")

Pour affiner la zone de recherche, tapez l’un des filtres de 1 lettre, suivi d’un espace, puis de l’élément que vous recherchez.

## <a name="error-list"></a>Liste d'erreurs

Après avoir défini la norme du langage C++ souhaitée et toutes les autres options du compilateur (propriétés du**projet**  >  **Properties**  >  **générales**), appuyez sur **Ctrl + Maj + B** pour compiler votre projet. Vous pouvez vous attendre à voir des erreurs et des avertissements sous forme de tildes rouges à différents endroits dans le code. Les erreurs apparaissent également dans le **liste d’erreurs**. Pour plus d’informations sur une erreur spécifique, cliquez sur le code d’erreur pour accéder à la page d’aide de la documentation. Les codes d’erreur qui commencent par « C » sont des erreurs du compilateur. Les codes qui commencent par « MSB » sont des erreurs MSBuild qui indiquent un problème avec la configuration du projet.

![Erreurs de compilateur et MSBuild dans Liste d’erreurs](media/compiler-error-list.png "Erreurs de compilateur et MSBuild dans Liste d’erreurs")

## <a name="document-health-indicator"></a>Indicateur d’intégrité du document

L’indicateur d’intégrité du document situé en bas de l’éditeur indique le nombre d’erreurs et d’avertissements dans le document actif, et vous permet de naviguer directement d’un avertissement ou d’une erreur à la suivante.

![Indicateur d’intégrité du document](media/document-health-indicator.png "Indicateur d’intégrité du document")

Dans de nombreux cas, vous trouverez plus d’informations sur une erreur spécifique dans la documentation sur les améliorations de l’historique des modifications et de la conformité de Visual Studio.

- [Améliorations de la conformité de C++](../overview/cpp-conformance-improvements.md)
- [Historique des modifications de Visual C++ 2003-2015](visual-cpp-change-history-2003-2015.md)
- [Vue d’ensemble des problèmes de mise à niveau potentiels](overview-of-potential-upgrade-issues-visual-cpp.md)

## <a name="use-code-analysis-to-modernize-your-code"></a>Utiliser l’analyse du code pour moderniser votre code

Lors de la mise à niveau, nous vous recommandons d’exécuter l’analyse du code sur votre projet afin que le code soit conforme au minimum aux règles Microsoft natives recommandées. Ces règles sont une combinaison de règles définies par Microsoft et d’un sous-ensemble de l' [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines). En les conformant, vous allez réduire ou éliminer les sources courantes des bogues et, en même temps, rendre votre code plus lisible et, par conséquent, plus facile à gérer. L’analyse du code à l’aide des règles Microsoft Native Recommended est activée par défaut. Vous pouvez activer des règles supplémentaires **Project**sous l’analyse du code des  >  **Propriétés**du projet  >  **Code Analysis**. Le code qui viole l’une des règles est marqué comme un avertissement et est souligné d’un tilde vert dans l’éditeur de code. Pointez sur le tilde pour afficher **une info** -bulle info-bulle qui décrit le problème.

![Info-bulle de l’analyse du code](media/code-analysis-tooltip.png "Avertissement de l’analyse du code")

Cliquez sur l’icône de filtre dans la colonne **code** pour choisir les avertissements à afficher.

![Filtres d’analyse du code dans Liste d’erreurs](media/code-analysis-filter.png "Filtres d’analyse du code dans Liste d’erreurs")

Les erreurs et avertissements liés à l’analyse du code s’affichent également dans le **liste d’erreurs** comme des erreurs du compilateur.

![Avertissements d’analyse du code dans Liste d’erreurs](media/code-analysis-error-list.png "Avertissements d’analyse du code dans Liste d’erreurs")

Vous pouvez modifier les règles actives et créer des ensembles de règles personnalisés. Pour plus d’informations sur l’utilisation de l’analyse du code, consultez [vue d’ensemble de l’analyse du code pour C/C++](../code-quality/code-analysis-for-c-cpp-overview.md).

## <a name="use-quick-actions-to-modernize-code"></a>Utiliser des actions rapides pour moderniser du code

L’éditeur de code fournit des actions rapides pour certaines recommandations courantes. Lorsque l’icône d’ampoule s’affiche, vous pouvez cliquer dessus pour afficher les actions rapides disponibles.

### <a name="convert-macros-to-constexpr-functions"></a>Convertir des macros en fonctions constexpr

L’illustration suivante montre l’utilisation de la macro appelée `AVERAGE` , qui a la colorisation sémantique par défaut. L’image affiche également l’info-bulle info-bulle qui s’affiche lorsque le curseur de la souris est placé sur celle-ci :

![Expansion macro Info Express](media/macro-expansion-quick-info.png "Expansion macro info-bulle Info Express")

Étant donné que l’utilisation des macros est déconseillée dans le C++ moderne, Visual Studio facilite la conversion des macros en **`constexpr`** fonctions :

1. Cliquez avec le bouton droit sur `AVERAGE` et choisissez **atteindre la définition**.
2. Cliquez sur l’icône du tournevis et choisissez **convertir la macro en constexpr**

   ![Macro action rapide à constexpr](media/quick-action-macro-to-constexpr.png "Macro action rapide à constexpr")

La macro est convertie comme indiqué ci-dessous :

![constexpr fonction)](media/constexpr-function.png "constexpr fonction)")

Et l’appel à `AVERAGE` est désormais coloré comme un appel de fonction, et le info-bulle Info Express affiche le type déduit de la fonction :

![appel de fonction constexpr](media/constexpr-function-call.png "appel de fonction constexpr")

### <a name="initialize-variables"></a>Initialiser les variables

Les variables non initialisées peuvent contenir des valeurs aléatoires entraînant des bogues sérieux. L’analyse du code signale ces instances et l’éditeur fournit une action rapide :

![Initialiser la variable](media/init-variable.png "Initialiser une action rapide sur une variable")

### <a name="convert-to-raw-string-literal"></a>Convertir en littéral de chaîne brut

Les littéraux de chaîne bruts sont moins sujets aux erreurs et plus pratiques à taper que les chaînes avec des caractères d’échappement incorporés. Cliquez avec le bouton droit sur une chaîne et choisissez **actions rapides** pour la convertir en littéral de chaîne brute.

![Littéral de chaîne brut](media/raw-string-literal.png "Littéral de chaîne brut")

La chaîne est convertie en : `R"(C:\Users\bjarnes\demo\output.txt)"` .
