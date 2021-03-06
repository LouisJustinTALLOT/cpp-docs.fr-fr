---
description: 'En savoir plus sur : génération d’applications isolées C/C++ et d’assemblys côte à côte'
title: Génération d'applications isolées C/C++ et d'assemblys côte à côte
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: a48e0e63b78e72d99241df84cdd9709198c1aa82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157072"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Génération d'applications isolées C/C++ et d'assemblys côte à côte

Visual Studio prend en charge un modèle de déploiement pour les applications clientes Windows en fonction de l’idée des [applications isolées](/windows/win32/SbsCs/isolated-applications) et des [assemblys côte à côte](/windows/win32/SbsCs/about-side-by-side-assemblies-). Par défaut, Visual Studio génère toutes les applications C/C++ natives en tant qu’applications isolées qui utilisent des [manifestes](/windows/win32/sbscs/manifests) pour décrire leurs dépendances sur les bibliothèques de Visual C++.

La création des programmes C/C++ en tant qu'applications isolées présente toute une palette d'avantages. Par exemple, une application isolée n'est pas affectée quand d'autres applications C/C++ installent ou désinstallent des bibliothèques Visual C++. Les bibliothèques Visual C++ utilisées par une application isolée peuvent encore être redistribuées dans le dossier local de l’application ou en étant installées dans le cache d’assembly natif (WinSxS). Toutefois, la maintenance des bibliothèques Visual C++ pour des applications déjà déployées peut-être simplifiée à l’aide d’un [fichier de configuration d’éditeur](/windows/win32/SbsCs/publisher-configuration). Le modèle de déploiement d'applications isolées permet de garantir plus aisément que les applications C/C++ qui s'exécutent sur un ordinateur spécifique utilisent la version la plus récente des bibliothèques Visual C++, tout en continuant de permettre aux administrateurs système et aux auteurs d'applications de contrôler la liaison explicite des versions des applications avec leur DLL dépendantes.

Cette section explique comment générer une application C/C++ en tant qu'application isolée et s'assurer qu'elle est liée aux bibliothèques Visual C++ à l'aide d'un manifeste. Les informations contenues dans cette section s’appliquent principalement aux applications C++ natives ou non managées. Pour plus d’informations sur le déploiement d’applications C++ natives créées avec Visual Studio, consultez [redistribution des fichiers de Visual C++](../windows/redistributing-visual-cpp-files.md).

## <a name="in-this-section"></a>Dans cette section

[Concepts d’applications isolées et d’assemblys côte à côte](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[Génération d’applications isolées C/C++](building-c-cpp-isolated-applications.md)

[Génération d’assemblys côte à côte C/C++](building-c-cpp-side-by-side-assemblies.md)

[Comment : générer des composants COM Registration-Free](how-to-build-registration-free-com-components.md)

[Comment : générer des applications isolées pour consommer des composants COM](how-to-build-isolated-applications-to-consume-com-components.md)

[Fonctionnement de la génération de manifestes pour les programmes C/C++](understanding-manifest-generation-for-c-cpp-programs.md)

[Résolution des problèmes d’applications isolées C/C++ et d’assemblys côte à côte](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>Sections connexes

[Applications isolées et assemblys côte à côte](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[Déploiement des applications de bureau](../windows/deploying-native-desktop-applications-visual-cpp.md)
