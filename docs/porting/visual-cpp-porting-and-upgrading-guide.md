---
title: Guide C++ de Portage et de mise à niveau Microsoft
description: Mettez à C++ niveau Microsoft code vers la dernière version de Visual Studio.
ms.date: 10/29/2019
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: d67c2665574242a46d697f6e9f24321556146958
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625682"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Guide C++ de Portage et de mise à niveau Microsoft

Cette rubrique fournit un guide pour la mise à C++ niveau de Microsoft code vers la dernière version de Visual Studio. Si vous effectuez une mise à niveau à partir d’un projet créé dans Visual Studio 2008 ou version antérieure, vous devez d’abord utiliser Visual Studio 2010 pour convertir le projet au format MSBuild, puis ouvrir le projet dans Visual Studio 2019. Pour les projets créés dans Visual Studio 2010 à 2015, il vous suffit d’ouvrir le projet dans Visual Studio 2019. Pour obtenir des instructions complètes, consultez [mise à niveau de C++ projets à partir de versions antérieures de Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

Les ensembles d’outils de Visual Studio 2015, Visual Studio 2017 et Visual Studio 2019 sont compatibles binaires, ce qui vous permet d’effectuer une mise à niveau vers une version plus récente du compilateur sans avoir à mettre à niveau les dépendances de bibliothèque. Pour plus d’informations, consultez [ C++ compatibilité binaire entre 2015 et 2019](binary-compat-2015-2017.md).

Lors de la mise à niveau de projets qui utilisent des bibliothèques Open source ou qui sont destinés à être exécutés sur plusieurs plateformes, nous vous recommandons de migrer vers un projet basé sur CMake. Pour plus d’informations, consultez [projets cmake dans Visual Studio](../build/cmake-projects-in-visual-studio.md) .

## <a name="reasons-to-upgrade-c-code"></a>Raisons justifiant C++ la mise à niveau du code

Si une application héritée s’exécute de manière satisfaisante, dans un environnement sécurisé et qu’elle n’est pas en cours de développement actif, il est possible qu’il n’y ait pas d’incentives pour la mettre à niveau. Toutefois, si une application nécessite une maintenance continue ou un nouveau développement de fonctionnalités, y compris des améliorations en matière de performances ou de sécurité, vous pouvez envisager de mettre à niveau le code pour l’une des raisons suivantes :

- Le même code peut s’exécuter plus rapidement en raison des optimisations du compilateur améliorées.

- Les C++ fonctionnalités et les pratiques de programmation modernes éliminent de nombreuses causes courantes des bogues et sont beaucoup plus faciles à gérer que les plus anciens idiomes de style C.

- Les temps de génération sont beaucoup plus rapides, en raison des améliorations des performances du compilateur et de l’éditeur de liens.

- Meilleure conformité aux normes. L’option du compilateur [/permissive-](../build/reference/permissive-standards-conformance.md) vous permet d’identifier le code qui était précédemment autorisé par C++ le compilateur Microsoft, mais qui n’est C++ pas conforme à la norme actuelle.

- Meilleure sécurité à l’exécution, notamment des fonctionnalités de la [bibliothèque Runtime C]() plus sécurisées et des fonctionnalités du compilateur, telles que la vérification de la [protection](../build/reference/guard-enable-guard-checks.md) et l’adressage des assainiurs (Visual Studio 2019 version 16,4).

## <a name="multitargeting-vs-upgrading"></a>MULTICIBLAGE et mise à niveau

Si la mise à niveau de votre base de code vers un nouvel ensemble d’outils n’est pas une option, vous pouvez toujours utiliser une version récente de Visual Studio pour générer et modifier des projets qui se compilent avec des bibliothèques et des ensembles d’outils plus anciens. Dans Visual Studio 2019, vous pouvez tirer parti de fonctionnalités telles que :

- les outils d’analyse statique modernes, C++ y compris les principaux outils de vérification et Clang-Tidy, permettent d’identifier les problèmes potentiels dans votre code source.

- la mise en forme automatique en fonction de votre choix de styles modernes peut aider à rendre le code hérité bien plus lisible.

Pour plus d’informations, consultez [Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](use-native-multi-targeting.md).

## <a name="in-this-section"></a>Dans cette section

|Titre|Description|
|-----------|-----------------|
|[Mise à C++ niveau de projets à partir de versions antérieures de Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Comment mettre à niveau votre base de code vers Visual Studio 2019 et V142 du compilateur.|
|[C++Compatibilité binaire entre 2015 et 2019](binary-compat-2015-2017.md)|Consommez les bibliothèques V140 en l’des projets V142.|
|[Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](use-native-multi-targeting.md)|Utilisez Visual Studio 2019 avec des compilateurs et des bibliothèques plus anciens.|
|[Historique des modifications de Visual C++ entre 2003 et 2015](visual-cpp-change-history-2003-2015.md)|Liste de toutes les modifications apportées aux C++ bibliothèques Microsoft et aux outils de génération de Visual Studio 2003 à 2015, qui peuvent nécessiter des modifications dans votre code.|
|[Nouveautés de Visual C++ entre 2003 et 2015](visual-cpp-what-s-new-2003-through-2015.md)|Toutes les informations sur les nouveautés de Microsoft C++ de visual studio 2003 à visual studio 2015.|
|[Portage et mise à niveau : exemples et études de cas](porting-and-upgrading-examples-and-case-studies.md)|Dans cette section, nous avons déplacé et mis à niveau plusieurs exemples et applications, puis présenté nos expériences et résultats. Cela vous donnera une idée de ce qu'impliquent les processus de déplacement et de mise à niveau. Nous donnons des conseils et astuces à suivre pendant toute la mise à niveau, et indiquons des solutions pour corriger certaines erreurs courantes.|
|[Portage vers la plateforme universelle Windows](porting-to-the-universal-windows-platform-cpp.md)|Contient des informations sur le déplacement de code vers Windows 10|
|[Introduction à Visual C++ pour les utilisateurs UNIX](introduction-to-visual-cpp-for-unix-users.md)|Fournit des informations aux utilisateurs UNIX qui débutent avec Visual C++ et souhaitent être plus productifs.|
|[Exécution de programmes Linux sur Windows](porting-from-unix-to-win32.md)|Présente les différentes options pour migrer des applications UNIX vers Windows.|

## <a name="see-also"></a>Voir aussi

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Nouveautés du compilateur C++ dans Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Améliorations de la conformité de C++ dans Visual Studio](../overview/cpp-conformance-improvements.md)<br/>
