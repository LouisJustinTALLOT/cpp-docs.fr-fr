---
description: 'En savoir plus sur : création d’un objet agrégé'
title: Création d’un objet agrégé
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
ms.openlocfilehash: e6efbf63e28d0477730a2d7c31ec91e9b75520e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153224"
---
# <a name="creating-an-aggregated-object"></a>Création d’un objet agrégé

L’agrégation délègue `IUnknown` les appels, en fournissant un pointeur vers l’objet externe `IUnknown` à l’objet interne.

## <a name="to-create-an-aggregated-object"></a>Pour créer un objet agrégé

1. Ajoutez un `IUnknown` pointeur à votre objet de classe et initialisez-le sur la valeur null dans le constructeur.

1. Remplacez [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) pour créer l’agrégat.

1. Utilisez le `IUnknown` pointeur, défini à l’étape 1, en tant que deuxième paramètre pour les macros [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) .

1. Remplacez [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) pour libérer le `IUnknown` pointeur.

> [!NOTE]
> Si vous utilisez et publiez une interface à partir de l’objet agrégé pendant `FinalConstruct` , vous devez ajouter la macro [DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) à la définition de votre objet de classe.

## <a name="see-also"></a>Voir aussi

[Notions de base des objets COM ATL](../atl/fundamentals-of-atl-com-objects.md)
