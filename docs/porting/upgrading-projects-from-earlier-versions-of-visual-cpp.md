---
title: Mettre à niveau des projets C++ à partir de versions antérieures de Visual Studio
description: Découvrez comment mettre à niveau des projets Microsoft C++ à partir de versions antérieures de Visual Studio.
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: 89c1df88aa8e533dd7d6e5312b1150468c905c18
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334232"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Mettre à niveau des projets C++ à partir de versions antérieures de Visual Studio

Pour mettre à niveau un projet créé dans une version antérieure de Visual Studio, il vous suffit d’ouvrir le projet dans la dernière version de Visual Studio. Visual Studio propose de mettre à niveau le projet vers le schéma actuel.

Si vous choisissez **non** , le projet n’est pas mis à niveau. Pour les projets créés dans Visual Studio 2010 et versions ultérieures, vous pouvez toujours utiliser le projet dans la version plus récente de Visual Studio. Il vous suffit de définir les propriétés de votre projet pour continuer à cibler l’ensemble d’outils antérieur. Si vous laissez l’ancienne version de Visual Studio sur votre ordinateur, son ensemble d’outils est disponible dans les versions ultérieures. Par exemple, si votre projet doit continuer à s’exécuter sous Windows XP, vous pouvez effectuer la mise à niveau vers Visual Studio 2019. Vous spécifiez ensuite l’ensemble d’outils comme v141_xp ou une version antérieure dans les propriétés de votre projet. Pour plus d’informations, consultez [Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](use-native-multi-targeting.md).

Si vous choisissez **Oui** , le projet est mis à niveau sur place. Elle ne peut pas être reconvertie dans la version antérieure. Dans les scénarios de mise à niveau, c’est la raison pour laquelle il est recommandé d’effectuer une copie de sauvegarde des fichiers projet et solution existants.

## <a name="upgrade-reports"></a>Mettre à niveau des rapports

Lorsque vous mettez à niveau un projet, vous recevez un rapport de mise à niveau. Le rapport est également enregistré dans votre dossier de projet en tant que UpgradeLog.htm. Le rapport de mise à niveau affiche un résumé des problèmes détectés lors de la conversion. Elle répertorie des informations sur les modifications apportées, notamment :

- Propriétés du projet.

- Fichiers include.

- Code qui ne se compile plus correctement en raison des améliorations de la conformité du compilateur ou des modifications apportées à la norme.

- Code qui s’appuie sur les fonctionnalités Visual Studio ou Windows qui ne sont plus disponibles. Ou des fichiers d’en-tête qui ne sont pas inclus dans une installation par défaut de Visual Studio ou qui ont été supprimés du produit.

- Code qui ne se compile plus en raison des modifications apportées aux API telles que les API renommées, les signatures de fonction modifiées ou les fonctions dépréciées.

- Code qui ne se compile plus en raison des modifications apportées aux diagnostics, comme un avertissement qui devient une erreur

- Erreurs de l’éditeur de liens en raison des bibliothèques qui ont été modifiées, en particulier quand/NODEFAULTLIB est utilisé.

- Erreurs d’exécution ou résultats inattendus en raison de changements de comportement.

- Erreurs qui ont été introduites dans les outils. Si vous rencontrez un problème, signalez-le à l’équipe Visual C++ par le biais de vos canaux de support habituels ou à l’aide de la page [communauté des développeurs Visual Studio C++](https://aka.ms/feedback/report?space=62) .

Certains projets et solutions mis à niveau peuvent être générés correctement sans modification. Toutefois, la plupart des projets nécessitent probablement des modifications des paramètres du projet et du code source. Il n’existe pas de méthode correcte pour résoudre ces problèmes, mais nous vous recommandons d’utiliser une approche progressive. Avant de commencer, consultez [vue d’ensemble des problèmes de mise à niveau potentiels](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) pour plus d’informations sur de nombreux types d’erreurs courantes.

1. Définissez l’ensemble d’outils de plateforme, la norme du langage C++ et la version de SDK Windows (le cas échéant) sur les versions préférées. ( **Projet**  >  **Propriétés**  >  de **Propriétés**  >  de configuration **Général** )

1. Si vous avez un grand nombre d’erreurs, vous pouvez désactiver temporairement certaines options lorsque vous les corrigez. Pour désactiver l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) option, utilisez les propriétés de **projet**  >  **Properties**  >  **Configuration des propriétés de configuration**  >  **C/C++**  >  **Language**. Pour désactiver l’option d' [analyse du code](../code-quality/code-analysis-for-c-cpp-overview.md) , utilisez propriétés de **projet**  >  **Properties**  >  **Propriétés de configuration**  >  **analyse du code**.

1. Vérifiez que toutes les dépendances sont présentes et que les chemins d’accès include ou les emplacements de bibliothèque sont corrects. ( **Projet**  >  **Propriétés**  >  de **Propriétés**  >  de configuration **Répertoires VC + +** )

1. Identifiez et corrigez les erreurs causées par des références aux API qui n’existent plus.

1. Corrigez toutes les erreurs restantes qui empêchent la compilation. Reportez-vous à [vue d’ensemble des problèmes de mise à niveau potentiels](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) pour les erreurs courantes.

1. Réactivez **`/permissive-`** et corrigez les nouvelles erreurs causées par un code non conforme qui a déjà été compilé dans MSVC.

1. Activez l’analyse du code pour identifier les problèmes potentiels ou les modèles de codage obsolètes qui ne sont plus considérés comme acceptables. Si l’analyse du code signale de nombreuses erreurs, vous pouvez désactiver certains des avertissements pour vous concentrer en priorité sur les plus importants. L’IDE peut aider à résoudre des problèmes rapides pour certains types de problèmes.

1. Pensez à d’autres opportunités pour la modernisation du code. Par exemple, remplacez les structures de données personnalisées et les algorithmes par des algorithmes de la bibliothèque C++ standard ou augmentez la bibliothèque open source. En utilisant des fonctionnalités standard, vous facilitez la gestion du code par d’autres personnes. Vous pouvez être certain que ce code a été correctement testé et revu par de nombreux experts sur le Comité des normes et la communauté C++ plus large.

Pour les erreurs difficiles à corriger, vous pouvez rechercher des solutions ou poser une question sur [Microsoft docs Q&a](/answers/topics/c%2B%2B.html). Pour les problèmes dans le compilateur et les outils C++, essayez le site Web de la [communauté des développeurs c++](https://aka.ms/vsfeedback/browsecpp) .

## <a name="in-this-section"></a>Dans cette section

[Vue d’ensemble des problèmes de mise à niveau potentiels](overview-of-potential-upgrade-issues-visual-cpp.md)\
[Mettre à niveau votre code vers le CRT universel](upgrade-your-code-to-the-universal-crt.md)\
[Mettre à jour WINVER et _WIN32_WINNT](modifying-winver-and-win32-winnt.md)\
[Corriger vos dépendances sur les éléments internes de bibliothèque](fix-your-dependencies-on-library-internals.md)\
[Problèmes de migration à virgule flottante](floating-point-migration-issues.md)\
[Fonctionnalités C++ dépréciées dans Visual Studio 2019](features-deprecated-in-visual-studio.md)\
[VCBuild et MSBuild](build-system-changes.md)\
[Portage de bibliothèques de tiers](porting-third-party-libraries.md)

## <a name="see-also"></a>Voir aussi

[Nouveautés de Visual C++ dans Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[Historique des modifications de Visual C++ 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Comportement non standard](../cpp/nonstandard-behavior.md)\
[Portage d’applications de données](../data/data-access-programming-mfc-atl.md)
