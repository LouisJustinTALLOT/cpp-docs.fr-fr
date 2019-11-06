---
title: Mettre C++ à niveau des projets à partir de versions antérieures de Visual Studio
description: Découvrez comment mettre à niveau des projets Microsoft C++ à partir de versions antérieures de Visual Studio.
ms.date: 10/29/2019
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: b317271a9cd0873e60a6dd9acd1b73a766aaea19
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627164"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Mettre C++ à niveau des projets à partir de versions antérieures de Visual Studio

Pour mettre à niveau un projet créé dans Visual Studio 2008 ou une version antérieure, vous devez d’abord utiliser Visual Studio 2010 pour convertir le projet du format VCBuild (. vcproj) au format MSBuild (. vcxproj). Pour plus d’informations, consultez [instructions pour Visual Studio 2008](use-native-multi-targeting.md#instructions-for-visual-studio-2008).

Pour mettre à niveau un projet créé dans Visual Studio 2010 ou une version ultérieure, il vous suffit d’ouvrir le projet dans la dernière version de Visual Studio. Visual Studio propose de mettre à niveau le projet vers le schéma actuel. Si vous choisissez **non**et que vous disposez de la version antérieure de Visual Studio sur votre ordinateur, vous pouvez travailler dans le projet dans une version plus récente de Visual Studio et continuer à cibler l’ensemble d’outils antérieur. Par exemple, si votre projet doit continuer à s’exécuter sur Windows XP, vous pouvez le mettre à niveau vers Visual Studio 2019, mais vous devez spécifier l’ensemble d’outils comme V141 ou version antérieure. Pour plus d’informations, consultez [Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](use-native-multi-targeting.md). Si vous choisissez **Oui**, le projet sera converti et ne pourra pas être reconverti dans la version antérieure. Par conséquent, dans les scénarios de mise à niveau, il est recommandé d’effectuer une copie des fichiers projet et solution existants.

## <a name="upgrade-reports"></a>Rapports de mise à niveau

Quand vous mettez à niveau un projet, un rapport de mise à niveau est généré et enregistré dans votre dossier de projet sous le nom UpgradeLog.htm. Le rapport de mise à niveau affiche un résumé des problèmes rencontrés et des informations sur les modifications apportées, notamment :

1. Propriétés de projet

2. Fichiers Include

3. Code qui ne se compile plus correctement en raison des améliorations de la conformité du compilateur ou des modifications apportées à la norme

4. Code qui fait appel à des fonctionnalités Visual Studio ou Windows qui ne sont plus disponibles, ou à des fichiers d’en-tête qui ne sont pas inclus dans une installation par défaut de Visual Studio ou qui ont été supprimés du produit.

5. Code qui ne se compile plus à cause des modifications apportées aux API (par exemple, API renommées, signatures de fonction modifiées ou fonctions déconseillées).

6. Code qui ne se compile plus en raison de modifications apportées aux diagnostics, comme un avertissement qui devient une erreur

7. Erreurs de l'éditeur de liens dues aux modifications de bibliothèques, en particulier quand /NODEFAULTLIB est utilisé.

8. Erreurs d'exécution ou résultats inattendus dus à des changements de comportement.

9. Erreurs qui ont été introduites dans les outils. Si vous rencontrez un problème, signalez-le à l’équipe Visual C++ par le biais de vos modes de contact du support technique habituels ou de la page [Communauté de développeurs Visual Studio C++](https://developercommunity.visualstudio.com/spaces/62/index.html).

Certains projets et solutions mis à niveau peuvent être générés correctement sans modification. Toutefois, la plupart des projets requièrent probablement des modifications des paramètres du projet et du code source. Il n’existe pas de méthode correcte pour corriger ces informations, mais il est recommandé d’utiliser un type d’approche échelonnée. Avant de commencer, consultez [vue d’ensemble des problèmes de mise à niveau potentiels](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) pour plus d’informations sur de nombreux types d’erreurs courantes.

 1. Définissez l’ensemble d’outils C++ de plateforme, le langage standard et la version de SDK Windows (le cas échéant) sur les versions souhaitées. ( **Propriétés** de la > de**projet** > **Propriétés de configuration** > **général**)
 1. Si vous avez un grand nombre d’erreurs, désactivez l’option [permissif](../build/reference/permissive-standards-conformance.md) ( **Propriétés** du**projet** >  > **Propriétés de configuration** > **langage** **CC++ /**  > ) et l’analyse du [code ](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)( **Propriétés** de la > de**projet** > **Propriétés de configuration** > analyse du **code**) temporairement pour réduire le nombre d’erreurs.
 1. Vérifiez que toutes les dépendances sont présentes et que les chemins d’accès include ou les emplacements de bibliothèque sont corrects. ( **Propriétés** du**projet** >  > **Propriétés de configuration** > **Répertoires VC + +** )
 1. Identifiez et corrigez les erreurs dues à des références aux API qui n’existent plus.
 1. Corrigez toutes les erreurs restantes qui empêchent la compilation. Reportez-vous à [vue d’ensemble des problèmes de mise à niveau potentiels](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) pour les erreurs courantes.
 1. Désactivez **-** la et corrigez les nouvelles erreurs qui apparaissent en raison du code non conforme qui a été précédemment compilé dans MSVC.
 1. Activez l’analyse du code pour identifier les problèmes potentiels ou les modèles de codage obsolètes qui ne sont plus considérés comme acceptables. Si l’analyse du code signale de nombreuses erreurs, vous pouvez désactiver certains des avertissements pour vous concentrer en priorité sur les plus importants. L’IDE peut aider à résoudre des problèmes rapides pour certains types de problèmes.
 1. Pensez à d’autres opportunités de la modernisation du code, par exemple en remplaçant des structures de données personnalisées et des C++ algorithmes par ceux de la bibliothèque standard ou de la bibliothèque open source de Boost. En utilisant les fonctionnalités standard, vous facilitez la gestion du code par d’autres personnes, ainsi que l’assurance que le code a été testé et revu par de nombreux experts du Comité des normes et de la C++ communauté plus large.

Pour les erreurs difficiles à corriger, essayez de rechercher ou de publier une question sur Stack Overflow [ C++ ](https://developercommunity.visualstudio.com/spaces/62/index.html)ou la communauté des développeurs.

## <a name="in-this-section"></a>Dans cette section

[Vue d’ensemble des problèmes de mise à niveau potentiels](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Mettre à niveau votre code vers la bibliothèque Universal CRT](upgrade-your-code-to-the-universal-crt.md)<br/>
[Mettre à jour WINVER et _WIN32_WINNT](modifying-winver-and-win32-winnt.md)<br/>
[Résoudre vos dépendances aux éléments internes de bibliothèque](fix-your-dependencies-on-library-internals.md)<br/>
[Problèmes de migration de virgule flottante](floating-point-migration-issues.md)<br/>
[C++fonctionnalités dépréciées dans Visual Studio 2019](features-deprecated-in-visual-studio.md)<br/>
[VCBuild et MSBuild](build-system-changes.md)<br/>
[Bibliothèques tierces de port](porting-third-party-libraries.md)<br/>

## <a name="see-also"></a>Voir aussi

[Nouveautés de Visual C++ dans Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historique des modifications de Visual C++ entre 2003 et 2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Comportement non standard](../cpp/nonstandard-behavior.md)<br/>
[Applications de données de port](../data/data-access-programming-mfc-atl.md)<br/>
