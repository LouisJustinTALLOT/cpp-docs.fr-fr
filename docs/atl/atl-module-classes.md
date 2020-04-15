---
title: Module ATL, classes
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 2b72cac0da06b70a40e01fcc75da52f1678f3f64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317375"
---
# <a name="atl-module-classes"></a>Module ATL, classes

Ce sujet traite des classes de modules qui étaient nouvelles dans ATL 7.0.

## <a name="ccommodule-replacement-classes"></a>Cours de remplacement CComModule

Versions antérieures de `CComModule`ATL utilisé . Dans ATL 7.0, `CComModule` la fonctionnalité est remplacée par plusieurs classes :

- [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) Contient les informations requises par la plupart des applications qui utilisent ATL. Contient le HINSTANCE du module et l’instance des ressources.

- [CAtlComModule](../atl/reference/catlcommodule-class.md) Contient les informations requises par les classes COM en ATL.

- [CAtlWinModule](../atl/reference/catlwinmodule-class.md) Contient les informations requises par les classes de fenêtre en ATL.

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) Contient la prise en charge pour le débogage d’interface.

- [CAtlModule](../atl/reference/catlmodule-class.md) Les `CAtlModule`classes dérivées suivantes sont personnalisées pour contenir les informations requises dans un type d’application particulier. La plupart des membres de ces classes peuvent être remplacés :

  - [CAtldllModuleT](../atl/reference/catldllmodulet-class.md) Utilisé dans les applications DLL. Fournit un code pour les exportations standard.

  - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) Utilisé dans les applications EXE. Fournit le code requis dans un EXE.

  - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) Fournit un support pour créer Windows NT et Windows 2000 Services.

`CComModule`est toujours disponible pour la compatibilité vers l’arrière.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Raisons de la distribution de la fonctionnalité CComModule

La fonctionnalité `CComModule` de a été distribuée dans plusieurs nouvelles classes pour les raisons suivantes:

- Rendre la fonctionnalité `CComModule` granulaire.

   La prise en charge des fonctionnalités COM, de fenêtre, de débogage d’interface et de fonctionnalités spécifiques à l’application (DLL ou EXE) est maintenant dans des classes séparées.

- Déclarez automatiquement l’exemple global de chacun de ces modules.

   Une instance globale des classes de modules requises est liée au projet.

- Supprimer la nécessité d’appeler les méthodes Init et Term.

   Les méthodes Init et Term sont passées dans les constructeurs et les destructeurs pour les classes de modules; il n’est plus nécessaire d’appeler Init et Term.

## <a name="see-also"></a>Voir aussi

[Concepts liés à la](../atl/active-template-library-atl-concepts.md)<br/>
[Vue d'ensemble des classes](../atl/atl-class-overview.md)
