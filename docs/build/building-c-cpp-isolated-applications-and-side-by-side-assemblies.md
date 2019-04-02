---
title: Génération d'applications isolées C/C++ et d'assemblys côte à côte
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: b962796c3bf32bc312d3047535ae90a40a37094d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772460"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Génération d'applications isolées C/C++ et d'assemblys côte à côte

Visual C++ prend en charge un modèle de déploiement pour les applications clientes Windows qui s’appuie sur l’idée des [applications isolées](/windows/desktop/SbsCs/isolated-applications) et des [assemblys côte à côte](/windows/desktop/SbsCs/about-side-by-side-assemblies-). Par défaut, Visual C++ génère toutes les applications C/C++ natives en tant qu’applications isolées qui utilisent des [manifestes](/windows/desktop/sbscs/manifests) pour décrire leurs dépendances envers des bibliothèques Visual C++.

La création des programmes C/C++ en tant qu'applications isolées présente toute une palette d'avantages. Par exemple, une application isolée n'est pas affectée quand d'autres applications C/C++ installent ou désinstallent des bibliothèques Visual C++. Les bibliothèques Visual C++ utilisées par une application isolée peuvent encore être redistribuées dans le dossier local de l’application ou en étant installées dans le cache d’assembly natif (WinSxS). Toutefois, la maintenance des bibliothèques Visual C++ pour des applications déjà déployées peut-être simplifiée à l’aide d’un [fichier de configuration d’éditeur](/windows/desktop/SbsCs/publisher-configuration). Le modèle de déploiement d'applications isolées permet de garantir plus aisément que les applications C/C++ qui s'exécutent sur un ordinateur spécifique utilisent la version la plus récente des bibliothèques Visual C++, tout en continuant de permettre aux administrateurs système et aux auteurs d'applications de contrôler la liaison explicite des versions des applications avec leur DLL dépendantes.

Cette section explique comment générer une application C/C++ en tant qu'application isolée et s'assurer qu'elle est liée aux bibliothèques Visual C++ à l'aide d'un manifeste. Les informations fournies dans cette section s'appliquent principalement aux applications Visual C++ natives ou non managées. Pour plus d’informations sur le déploiement d’applications natives générées avec Visual C++, consultez [Redistributing Visual C++ Files](../windows/redistributing-visual-cpp-files.md).

## <a name="in-this-section"></a>Dans cette section

[Concepts d’applications isolées et d’assemblys côte à côte](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[Génération d’applications isolées C/C++](building-c-cpp-isolated-applications.md)

[Génération d’assemblys côte à côte C/C++](building-c-cpp-side-by-side-assemblies.md)

[Guide pratique pour générer des composants COM sans inscription](how-to-build-registration-free-com-components.md)

[Guide pratique pour générer des applications isolées afin de consommer des composants COM](how-to-build-isolated-applications-to-consume-com-components.md)

[Présentation de la génération de manifeste pour les programmes C/C++](understanding-manifest-generation-for-c-cpp-programs.md)

[Dépannage d’applications isolées et d’assemblys côte à côte C/C++](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>Rubriques connexes

[Applications isolées et assemblys côte à côte](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[Déploiement des applications de bureau](../windows/deploying-native-desktop-applications-visual-cpp.md)