---
title: Module ATL, classes
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 2fe659b47893f821aab4cda31ab1a4e9a6788ec6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252068"
---
# <a name="atl-module-classes"></a>Module ATL, classes

Cette rubrique traite des classes du module qui étaient nouvelles dans ATL 7.0.

## <a name="ccommodule-replacement-classes"></a>Classes de remplacement de CComModule

Les versions antérieures de ATL utilisé `CComModule`. Dans ATL 7.0, `CComModule` fonctionnalité est remplacée par plusieurs classes :

- [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) contient les informations requises par la plupart des applications qui utilisent ATL. Contient l’HINSTANCE du module et l’instance de ressource.

- [CAtlComModule](../atl/reference/catlcommodule-class.md) contient les informations requises par les classes COM dans ATL.

- [CAtlWinModule](../atl/reference/catlwinmodule-class.md) contient les informations requises par les classes de fenêtrage dans ATL.

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) contient la prise en charge pour le débogage de l’interface.

- [CAtlModule](../atl/reference/catlmodule-class.md) suit `CAtlModule`-classes dérivées sont personnalisées pour contenir les informations requises dans un type d’application particulier. La plupart des membres de ces classes peuvent être remplacées :

   - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) utilisés dans les applications de la DLL. Fournit du code pour les exportations standards.

   - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) utilisé dans les applications EXE. Fournit le code requis dans un fichier EXE.

   - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) prend en charge pour créer de Windows NT et Windows 2000 Services.

`CComModule` est toujours disponible pour la compatibilité descendante.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Raisons de la distribution de la fonctionnalité CComModule

La fonctionnalité de `CComModule` a été distribuée dans plusieurs nouvelles classes pour les raisons suivantes :

- Vérifiez la fonctionnalité dans `CComModule` granulaire.

   Prise en charge de COM, le fenêtrage, débogage de l’interface et les fonctionnalités (DLL ou EXE) spécifique à l’application est maintenant dans des classes distinctes.

- Déclarer automatiquement l’instance globale de chacun de ces modules.

   Une instance globale des classes du module requis est liée au projet.

- Supprimer la nécessité de l’appel de méthodes Init et terme.

   Les méthodes Init et Term ont déplacés dans les constructeurs et les destructeurs des classes de module ; Il n’est plus nécessaire de les appeler à terme.

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)<br/>
[Vue d’ensemble de la classe](../atl/atl-class-overview.md)
