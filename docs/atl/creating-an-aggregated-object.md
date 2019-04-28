---
title: Création d’un objet agrégé
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
ms.openlocfilehash: 4be8d0e852da91b58125dc01d44eed4560b2b8d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250756"
---
# <a name="creating-an-aggregated-object"></a>Création d’un objet agrégé

Les délégués d’agrégation `IUnknown` appels, en fournissant un pointeur vers l’objet externe `IUnknown` à l’objet interne.

## <a name="to-create-an-aggregated-object"></a>Pour créer un objet agrégé

1. Ajouter un `IUnknown` pointeur à votre classe d’objet et l’initialiser avec la valeur NULL dans le constructeur.

1. Substituer [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) pour créer l’agrégat.

1. Utilisez le `IUnknown` pointeur, défini à l’étape 1, comme le deuxième paramètre pour le [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) macros.

1. Substituer [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) pour libérer le `IUnknown` pointeur.

> [!NOTE]
> Si vous utilisez et libérez une interface à partir de l’objet agrégée pendant `FinalConstruct`, vous devez ajouter le [macro DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) macro à la définition de votre objet de classe.

## <a name="see-also"></a>Voir aussi

[Principes de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)
