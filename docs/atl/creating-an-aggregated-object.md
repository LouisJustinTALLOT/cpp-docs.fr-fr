---
title: Création d’un objet agrégé | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9e11db0a9752ae7f88c5b1b21b81f0bb4c8a20f
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861224"
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

