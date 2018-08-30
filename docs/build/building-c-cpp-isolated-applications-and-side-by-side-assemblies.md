---
title: Génération C/C++ d’Applications isolées et assemblys côte à côte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8d806af709d6d6e2a5754bc80a34a473900177f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212910"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Génération d'applications isolées C/C++ et d'assemblys côte à côte
Visual C++ prend en charge un modèle de déploiement pour les applications clientes Windows basées sur l’idée de [d’applications isolées](/windows/desktop/SbsCs/isolated-applications) et [les assemblys côte à côte](/windows/desktop/SbsCs/about-side-by-side-assemblies-). Par défaut, Visual C++ génère toutes les applications C/C++ natives comme des applications isolées qui utilisent [manifestes](https://msdn.microsoft.com/library/aa375365) pour décrire leurs dépendances envers des bibliothèques Visual C++.  
  
 La création des programmes C/C++ en tant qu'applications isolées présente toute une palette d'avantages. Par exemple, une application isolée n'est pas affectée quand d'autres applications C/C++ installent ou désinstallent des bibliothèques Visual C++. Bibliothèques Visual C++ utilisées par une application isolée peuvent encore être redistribuées dans le dossier local soit l’application ou par installation dans le cache d’assembly natif (WinSxS) ; Toutefois, l’entretien des bibliothèques Visual C++ pour les applications déjà déployées peuvent être simplifiées en utilisant un [fichier de configuration de serveur de publication](/windows/desktop/SbsCs/publisher-configuration). Le modèle de déploiement d'applications isolées permet de garantir plus aisément que les applications C/C++ qui s'exécutent sur un ordinateur spécifique utilisent la version la plus récente des bibliothèques Visual C++, tout en continuant de permettre aux administrateurs système et aux auteurs d'applications de contrôler la liaison explicite des versions des applications avec leur DLL dépendantes.  
  
 Cette section explique comment générer une application C/C++ en tant qu'application isolée et s'assurer qu'elle est liée aux bibliothèques Visual C++ à l'aide d'un manifeste. Les informations fournies dans cette section s'appliquent principalement aux applications Visual C++ natives ou non managées. Pour plus d’informations sur le déploiement d’applications natives générées avec Visual C++, consultez [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Concepts d’applications isolées et d’assemblys côte à côte](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)  
  
 [Génération d’applications isolées C/C++](../build/building-c-cpp-isolated-applications.md)  
  
 [Génération d’assemblys côte à côte C/C++](../build/building-c-cpp-side-by-side-assemblies.md)  
  
 [Guide pratique pour générer des composants COM sans inscription](../build/how-to-build-registration-free-com-components.md)  
  
 [Guide pratique pour générer des applications isolées pour consommer des composants COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
 [Présentation de la génération de manifeste pour les programmes C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)  
  
 [Dépannage d’applications isolées et d’assemblys côte à côte C/C++](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Applications isolées et les assemblys côte à côte](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)  
  
 [Déploiement des applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md)