---
title: Module ATL, Classes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 777d81fbe1de48289863fda00591a5328b40cf4c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356603"
---
# <a name="atl-module-classes"></a>Module ATL, classes
Cette rubrique décrit les classes du module qui étaient nouvelles dans ATL 7.0.  
  
## <a name="ccommodule-replacement-classes"></a>Classes de remplacement de CComModule  
 Les versions antérieures de ATL utilisé `CComModule`. Dans ATL 7.0, `CComModule` fonctionnalité est remplacée par plusieurs classes :  
  
-   [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) contient les informations requises par la plupart des applications qui utilisent ATL. Contient l’HINSTANCE du module et l’instance de ressource.  
  
-   [CAtlComModule](../atl/reference/catlcommodule-class.md) contient des informations requises par les classes COM dans ATL.  
  
-   [CAtlWinModule](../atl/reference/catlwinmodule-class.md) contient des informations requises par les classes de fenêtrage dans ATL.  
  
-   [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) contient la prise en charge pour le débogage de l’interface.  
  
-   [CAtlModule](../atl/reference/catlmodule-class.md) suit `CAtlModule`-classes dérivées personnalisées et contiennent les informations requises dans un type particulier d’application. La plupart des membres de ces classes peuvent être substituées :  
  
    -   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) utilisée dans les applications de la DLL. Fournit du code pour les exportations standards.  
  
    -   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) utilisé dans les applications EXE. Fournit le code requis dans un fichier EXE.  
  
    -   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) fournit la prise en charge pour créer des Services Windows 2000 et Windows NT.  
  
 `CComModule` est toujours disponible pour la compatibilité descendante.  
  
## <a name="reasons-for-distributing-ccommodule-functionality"></a>Raisons de la distribution de la fonctionnalité CComModule  
 La fonctionnalité de `CComModule` a été distribuée dans plusieurs nouvelles classes pour les raisons suivantes :  
  
-   Vérifiez les fonctionnalités dans `CComModule` granulaire.  
  
     Prise en charge de COM, fenêtrage, débogage de l’interface et les fonctionnalités (DLL ou EXE) spécifiques à l’application est maintenant dans des classes séparées.  
  
-   Déclarer automatiquement l’instance globale de chacun de ces modules.  
  
     Une instance globale de classes du module requis est liée au projet.  
  
-   Supprimer la nécessité de l’appel de méthodes Init et Term.  
  
     Méthodes Init et Term ont déplacés dans les constructeurs et les destructeurs des classes de module ; Il n’est plus nécessaire de les appeler à terme.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)   
 [Vue d’ensemble de la classe](../atl/atl-class-overview.md)

