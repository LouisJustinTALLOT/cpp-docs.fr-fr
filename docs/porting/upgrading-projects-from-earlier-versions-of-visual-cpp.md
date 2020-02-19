---
title: Mettre C++ à niveau des projets à partir de versions antérieures de Visual Studio
description: Découvrez comment mettre à niveau des projets Microsoft C++ à partir de versions antérieures de Visual Studio.
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: bc9fb5628c1a628b91f306c346f2bbb1dea13de8
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416108"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Mettre C++ à niveau des projets à partir de versions antérieures de Visual Studio

Pour mettre à niveau un projet créé dans une version antérieure de Visual Studio, il vous suffit d’ouvrir le projet dans la dernière version de Visual Studio. Visual Studio propose de mettre à niveau le projet vers le schéma actuel.

Si vous choisissez **non**, le projet n’est pas mis à niveau. Pour les projets créés dans Visual Studio 2010 et versions ultérieures, vous pouvez toujours utiliser le projet dans la version plus récente de Visual Studio. Il vous suffit de définir les propriétés de votre projet pour continuer à cibler l’ensemble d’outils antérieur. Si vous laissez l’ancienne version de Visual Studio sur votre ordinateur, son ensemble d’outils est disponible dans les versions ultérieures. Par exemple, si votre projet doit continuer à s’exécuter sous Windows XP, vous pouvez effectuer la mise à niveau vers Visual Studio 2019. Vous spécifiez ensuite l’ensemble d’outils comme v141_xp ou une version antérieure dans les propriétés de votre projet. Pour plus d’informations, consultez [Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](use-native-multi-targeting.md).

Si vous choisissez **Oui**, le projet est mis à niveau sur place. Elle ne peut pas être reconvertie dans la version antérieure. Dans les scénarios de mise à niveau, c’est la raison pour laquelle il est recommandé d’effectuer une copie de sauvegarde des fichiers projet et solution existants.

## <a name="upgrade-reports"></a>Mettre à niveau des rapports

Lorsque vous mettez à niveau un projet, vous recevez un rapport de mise à niveau. Le rapport est également enregistré dans le dossier de votre projet sous le UpgradeLog. htm. Le rapport de mise à niveau affiche un résumé des problèmes détectés lors de la conversion. Elle répertorie des informations sur les modifications apportées, notamment :

- Propriétés du projet.

- Fichiers include.

- Code qui ne se compile plus correctement en raison des améliorations de la conformité du compilateur ou des modifications apportées à la norme.

- Code qui s’appuie sur les fonctionnalités Visual Studio ou Windows qui ne sont plus disponibles. Ou des fichiers d’en-tête qui ne sont pas inclus dans une installation par défaut de Visual Studio ou qui ont été supprimés du produit.

- Code qui ne se compile plus en raison des modifications apportées aux API telles que les API renommées, les signatures de fonction modifiées ou les fonctions dépréciées.

- Code qui ne se compile plus en raison des modifications apportées aux diagnostics, comme un avertissement qui devient une erreur

- Erreurs de l’éditeur de liens en raison des bibliothèques qui ont été modifiées, en particulier quand/NODEFAULTLIB est utilisé.

- Erreurs d’exécution ou résultats inattendus en raison de changements de comportement.

- Erreurs qui ont été introduites dans les outils. Si vous rencontrez un problème, signalez-le à C++ l’équipe Visual via vos canaux de support habituels ou à l’aide de la page [communauté des développeurs Visual Studio C++ ](https://developercommunity.visualstudio.com/spaces/62/index.html) .

Certains projets et solutions mis à niveau peuvent être générés correctement sans modification. Toutefois, la plupart des projets nécessitent probablement des modifications des paramètres du projet et du code source. Il n’existe pas de méthode correcte pour résoudre ces problèmes, mais nous vous recommandons d’utiliser une approche progressive. Avant de commencer, consultez [vue d’ensemble des problèmes de mise à niveau potentiels](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) pour plus d’informations sur de nombreux types d’erreurs courantes.

1. Définissez l’ensemble d’outils C++ de plateforme, le langage standard et la version de SDK Windows (le cas échéant) sur les versions préférées. ( **Propriétés** de la > de**projet** > **Propriétés de configuration** > **général**)

1. Si vous avez un grand nombre d’erreurs, vous pouvez désactiver temporairement certaines options lorsque vous les corrigez. Pour désactiver l’option [/permissive-](../build/reference/permissive-standards-conformance.md) , utilisez les **Propriétés** de **projet** >  > **Propriétés de configuration** > **langage** **C/C++**  > . Pour désactiver l’option [d’analyse du code](/cpp/code-quality/code-analysis-for-c-cpp-overview) , utilisez les **Propriétés** de > de **projet** > **Propriétés de configuration** > l’analyse du **code**.

1. Vérifiez que toutes les dépendances sont présentes et que les chemins d’accès include ou les emplacements de bibliothèque sont corrects. ( **Propriétés** du**projet** >  > **Propriétés de configuration** > **Répertoires VC + +** )

1. Identifiez et corrigez les erreurs causées par des références aux API qui n’existent plus.

1. Corrigez toutes les erreurs restantes qui empêchent la compilation. Reportez-vous à [vue d’ensemble des problèmes de mise à niveau potentiels](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) pour les erreurs courantes.

1. Réactivez **/permissive-** et corrigez les nouvelles erreurs causées par du code non conforme qui a été précédemment compilé dans MSVC.

1. Activez l’analyse du code pour identifier les problèmes potentiels ou les modèles de codage obsolètes qui ne sont plus considérés comme acceptables. Si l’analyse du code signale de nombreuses erreurs, vous pouvez désactiver certains des avertissements pour vous concentrer en priorité sur les plus importants. L’IDE peut aider à résoudre des problèmes rapides pour certains types de problèmes.

1. Pensez à d’autres opportunités pour la modernisation du code. Par exemple, remplacez les structures de données personnalisées et les algorithmes C++ par des algorithmes de la bibliothèque standard, ou augmentez la bibliothèque open source. En utilisant des fonctionnalités standard, vous facilitez la gestion du code par d’autres personnes. Vous pouvez être certain que ce code a été correctement testé et revu par de nombreux experts du Comité des normes et de la C++ communauté plus large.

Pour les erreurs difficiles à corriger, essayez de rechercher ou de publier une question sur Stack Overflow [ C++ ](https://developercommunity.visualstudio.com/spaces/62/index.html)ou la communauté des développeurs.

## <a name="in-this-section"></a>Contenu de cette section

[Vue d’ensemble des problèmes de mise à niveau potentiels](overview-of-potential-upgrade-issues-visual-cpp.md)\
[Mettez à niveau votre code vers la\ Universal CRT](upgrade-your-code-to-the-universal-crt.md)
[Mettre à jour winver et _WIN32_WINNT](modifying-winver-and-win32-winnt.md)\
[Corriger vos dépendances sur les éléments internes de bibliothèque](fix-your-dependencies-on-library-internals.md)\
[Problèmes de migration à virgule flottante](floating-point-migration-issues.md)\
[fonctionnalités dépréciées dans Visual Studio 2019\ C++ ](features-deprecated-in-visual-studio.md)
[VCBUILD et\ MSBuild](build-system-changes.md)
[Bibliothèques tierces de port](porting-third-party-libraries.md)

## <a name="see-also"></a>Voir aussi

[Nouveautés de Visual C++ Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[Historique C++ des modifications visuelles 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Comportement non standard](../cpp/nonstandard-behavior.md)\
[Applications de données de port](../data/data-access-programming-mfc-atl.md)
