---
title: Spécification des Pages de propriétés (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- ISpecifyPropertyPages
dev_langs:
- C++
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f80abd3b6270f105fecd7ef8b9988a379901b541
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860210"
---
# <a name="specifying-property-pages"></a>Spécification des Pages de propriétés

Lorsque vous créez un contrôle ActiveX, vous devez souvent à associer à des pages de propriétés qui peuvent être utilisés pour définir les propriétés de votre contrôle. Contrôler l’utilisation de conteneurs le `ISpecifyPropertyPages` interface pour trouver les pages de propriété peuvent être utilisées pour définir les propriétés de votre contrôle. Vous devez implémenter cette interface sur votre contrôle.

Pour implémenter `ISpecifyPropertyPages` à l’aide d’ATL, procédez comme suit :

1. Dérivez votre classe de [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md).

1. Ajoutez une entrée pour `ISpecifyPropertyPages` au mappage COM de votre classe.

1. Ajouter un [PROP_PAGE](reference/property-map-macros.md#prop_page) entrée dans le mappage de propriété pour chaque page associée à votre contrôle.

> [!NOTE]
> Lors de la génération d’un contrôle standard en utilisant le [Assistant contrôle ATL](../atl/reference/atl-control-wizard.md), vous devez uniquement ajouter les entrées PROP_PAGE au mappage de propriété. L’Assistant génère le code nécessaire pour les autres étapes.

Les conteneurs valides affichent les pages de propriétés spécifié dans le même ordre que les entrées PROP_PAGE dans le mappage de propriété. En règle générale, vous devez placer les entrées de page de propriétés standard après les entrées pour vos pages personnalisées dans le mappage de propriété, afin que les utilisateurs voient les pages spécifiques à votre contrôle tout d’abord.

## <a name="example"></a>Exemple

La classe suivante pour un calendrier de contrôles utilise le `ISpecifyPropertyPages` interface pour signaler aux conteneurs que ses propriétés peuvent être définies à l’aide d’une page de dates personnalisée et de la page stock de couleurs.

[!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]

## <a name="see-also"></a>Voir aussi

[Pages de propriétés](../atl/atl-com-property-pages.md)<br/>
[Exemple ATLPages](../visual-cpp-samples.md)
