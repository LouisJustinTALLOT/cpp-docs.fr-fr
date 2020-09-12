---
title: Guide de Portage et de mise à niveau de Microsoft C++
description: Mettez à niveau le code Microsoft C++ vers la dernière version de Visual Studio.
ms.date: 09/10/2020
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: b6cd3461ee16a44162fdb641170a2f05d9b77369
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039532"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Guide de Portage et de mise à niveau de Microsoft C++

Cet article fournit un guide pour la mise à niveau du code Microsoft C++ vers la dernière version de Visual Studio. Pour les projets créés dans Visual Studio 2010 à 2015, il vous suffit d’ouvrir le projet dans Visual Studio 2019. Vous pouvez mettre à niveau un projet Visual Studio 2008 ou version antérieure en deux étapes. Utilisez Visual Studio 2010 pour convertir le projet au format MSBuild en premier. Ouvrez ensuite le projet dans Visual Studio 2019. Pour obtenir des instructions complètes, consultez [mise à niveau de projets C++ à partir de versions antérieures de Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

Les ensembles d’outils de Visual Studio 2015, Visual Studio 2017 et Visual Studio 2019 sont compatibles binaires. Vous pouvez maintenant effectuer une mise à niveau vers une version plus récente du compilateur sans avoir à mettre à niveau vos dépendances de bibliothèque. Pour plus d’informations, consultez [compatibilité binaire C++ 2015-2019](binary-compat-2015-2017.md).

Lors de la mise à niveau de projets qui utilisent des bibliothèques Open source ou qui sont destinés à être exécutés sur plusieurs plateformes, nous vous recommandons de migrer vers un projet basé sur CMake. Pour plus d’informations, consultez [projets cmake dans Visual Studio](../build/cmake-projects-in-visual-studio.md) .

## <a name="reasons-to-upgrade-c-code"></a>Raisons justifiant la mise à niveau du code C++

Si une application héritée s’exécute de manière satisfaisante, dans un environnement sécurisé et qu’elle n’est pas en cours de développement actif, il peut ne pas y avoir d’incentives pour la mettre à niveau. Toutefois, envisagez une mise à niveau dans les cas suivants : votre application nécessite une maintenance continue. Ou vous effectuez de nouveaux développements de fonctionnalités ou Améliorez les performances ou la sécurité. Une mise à niveau offre les avantages suivants :

- Le même code peut s’exécuter plus rapidement, car nous avons amélioré les optimisations du compilateur.

- Les fonctionnalités C++ modernes et les pratiques de programmation éliminent de nombreuses causes courantes des bogues et génèrent du code qui est beaucoup plus facile à gérer que les idiomes de style C plus anciens.

- Les temps de génération sont plus rapides, en raison des améliorations des performances du compilateur et de l’éditeur de liens.

- Meilleure conformité aux normes. L’option du compilateur [/permissive-](../build/reference/permissive-standards-conformance.md) vous aide à identifier le code qui n’est pas conforme à la norme C++ actuelle. Le [nouveau préprocesseur](../preprocessor/preprocessor-experimental-overview.md) prend également en charge la conformité du code.

- Meilleure sécurité à l’exécution, y compris les fonctionnalités plus sécurisées de la [bibliothèque Runtime C](../c-runtime-library/security-features-in-the-crt.md) . Et les fonctionnalités du compilateur, telles que la vérification de la [protection](../build/reference/guard-enable-guard-checks.md) et l’adressage des assainiurs (nouveauté de Visual Studio 2019 version 16,4).

## <a name="multitargeting-vs-upgrading"></a>MULTICIBLAGE et mise à niveau

La mise à niveau de votre base de code vers un nouvel ensemble d’outils n’est peut-être pas une option pour vous. Vous pouvez toujours utiliser la dernière version de Visual Studio pour générer et modifier des projets qui utilisent des bibliothèques et des ensembles d’outils plus anciens. Dans Visual Studio 2019, vous pouvez tirer parti de fonctionnalités telles que :

- des outils d’analyse statique modernes, y compris les C++ Core Guidelines les consigneurs et Clang-Tidy, pour aider à identifier les problèmes potentiels dans votre code source.

- la mise en forme automatique en fonction de votre choix de styles modernes peut aider à rendre le code hérité bien plus lisible.

Pour plus d’informations, consultez [Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](use-native-multi-targeting.md).

## <a name="in-this-section"></a>Contenu de cette section

|Titre|Description|
|-----------|-----------------|
|[Mise à niveau de projets C++ à partir de versions antérieures de Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Comment mettre à niveau votre base de code vers Visual Studio 2019 et V142 du compilateur.|
|[Outils IDE pour la mise à niveau du code C++](ide-tools-for-upgrading-code.md)|Fonctionnalités IDE utiles qui facilitent le processus de mise à niveau.|
|[Compatibilité binaire C++ 2015-2019](binary-compat-2015-2017.md)|Consommez les bibliothèques V140 et V141 en l’des projets V142.|
|[Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](use-native-multi-targeting.md)|Utilisez Visual Studio 2019 avec des compilateurs et des bibliothèques plus anciens.|
|[Historique des modifications de Visual C++ entre 2003 et 2015](visual-cpp-change-history-2003-2015.md)|Liste de toutes les modifications apportées aux bibliothèques Microsoft C++ et aux outils de génération de Visual Studio 2003 à 2015, qui peuvent nécessiter des modifications dans votre code.|
|[Nouveautés de Visual C++ entre 2003 et 2015](visual-cpp-what-s-new-2003-through-2015.md)|Toutes les informations sur les nouveautés de Microsoft C++ de Visual Studio 2003 à Visual Studio 2015.|
|[Portage et mise à niveau : exemples et études de cas](porting-and-upgrading-examples-and-case-studies.md)|Dans cette section, nous avons déplacé et mis à niveau plusieurs exemples et applications, puis présenté nos expériences et résultats. Ces articles vous donnent une idée de ce qui est impliqué dans le processus de Portage et de mise à niveau. Nous donnons des conseils et astuces à suivre pendant toute la mise à niveau, et indiquons des solutions pour corriger certaines erreurs courantes.|
|[Portage vers la plateforme universelle Windows](porting-to-the-universal-windows-platform-cpp.md)|Contient des informations sur le déplacement de code vers Windows 10|
|[Introduction à Visual C++ pour les utilisateurs UNIX](introduction-to-visual-cpp-for-unix-users.md)|Fournit des informations aux utilisateurs UNIX qui débutent avec Visual C++ et souhaitent être plus productifs.|
|[Exécution de programmes Linux sur Windows](porting-from-unix-to-win32.md)|Présente les différentes options pour migrer des applications UNIX vers Windows.|

## <a name="see-also"></a>Voir aussi

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Nouveautés du compilateur C++ dans Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Améliorations de la conformité de C++ dans Visual Studio](../overview/cpp-conformance-improvements.md)<br/>
