---
description: 'En savoir plus sur : classes de module ATL'
title: Module ATL, classes
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 16c38a6a38f4179e5846a445bd9573e7dc4500f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163299"
---
# <a name="atl-module-classes"></a>Module ATL, classes

Cette rubrique décrit les classes de module qui ont été introduites dans ATL 7,0.

## <a name="ccommodule-replacement-classes"></a>Classes de remplacement CComModule

Versions antérieures d’ATL utilisées `CComModule` . Dans ATL 7,0, les `CComModule` fonctionnalités sont remplacées par plusieurs classes :

- [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) Contient les informations requises par la plupart des applications qui utilisent ATL. Contient le HINSTANCE du module et de l’instance de ressource.

- [CAtlComModule](../atl/reference/catlcommodule-class.md) Contient les informations requises par les classes COM dans ATL.

- [CAtlWinModule](../atl/reference/catlwinmodule-class.md) Contient les informations requises par les classes de fenêtrage dans ATL.

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) Contient la prise en charge du débogage d’interface.

- [CAtlModule](../atl/reference/catlmodule-class.md) Les `CAtlModule` classes dérivées suivantes sont personnalisées pour contenir les informations requises dans un type d’application particulier. La plupart des membres de ces classes peuvent être substitués :

  - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) Utilisé dans les applications DLL. Fournit du code pour les exportations standard.

  - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) Utilisé dans les applications EXE. Fournit le code requis dans un EXE.

  - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) Prend en charge la création de services Windows NT et Windows 2000.

`CComModule` est toujours disponible pour la compatibilité descendante.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Raisons de la distribution de la fonctionnalité CComModule

Les fonctionnalités de `CComModule` ont été distribuées dans plusieurs nouvelles classes pour les raisons suivantes :

- Rendez la fonctionnalité plus `CComModule` granulaire.

   La prise en charge des fonctionnalités COM, de fenêtrage, de débogage d’interface et spécifiques à l’application (DLL ou EXE) est désormais dans des classes distinctes.

- Déclarez automatiquement l’instance globale de chacun de ces modules.

   Une instance globale des classes de module requises est liée au projet.

- Éliminez la nécessité d’appeler les méthodes Init et term.

   Les méthodes Init et term ont été déplacées dans les constructeurs et les destructeurs pour les classes de module ; Il n’est plus nécessaire d’appeler init et term.

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)<br/>
[Vue d'ensemble des classes](../atl/atl-class-overview.md)
