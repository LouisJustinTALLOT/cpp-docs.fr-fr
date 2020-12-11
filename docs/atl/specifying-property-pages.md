---
description: 'En savoir plus sur : spécification des pages de propriétés'
title: Spécification des pages de propriétés (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
ms.openlocfilehash: 171440dde11178c85d1f636874b0b161691cb9cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157423"
---
# <a name="specifying-property-pages"></a>Spécification des pages de propriétés

Lorsque vous créez un contrôle ActiveX, vous devez souvent l’associer à des pages de propriétés qui peuvent être utilisées pour définir les propriétés de votre contrôle. Les conteneurs de contrôle utilisent l' `ISpecifyPropertyPages` interface pour déterminer les pages de propriétés qui peuvent être utilisées pour définir les propriétés de votre contrôle. Vous devrez implémenter cette interface sur votre contrôle.

Pour implémenter `ISpecifyPropertyPages` à l’aide d’ATL, procédez comme suit :

1. Dérivez votre classe de [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md).

1. Ajoutez une entrée pour `ISpecifyPropertyPages` au mappage com de votre classe.

1. Ajoutez une entrée [PROP_PAGE](reference/property-map-macros.md#prop_page) au mappage des propriétés pour chaque page associée à votre contrôle.

> [!NOTE]
> Lors de la génération d’un contrôle standard à l’aide de l' [Assistant contrôle ATL](../atl/reference/atl-control-wizard.md), vous devez uniquement ajouter les entrées PROP_PAGE au mappage de propriétés. L’Assistant génère le code nécessaire pour les autres étapes.

Les conteneurs de comportement correct affichent les pages de propriétés spécifiées dans le même ordre que les entrées PROP_PAGE dans le mappage de propriété. En règle générale, vous devez placer les entrées de la page de propriétés standard après les entrées de vos pages personnalisées dans le mappage des propriétés, afin que les utilisateurs voient d’abord les pages spécifiques à votre contrôle.

## <a name="example"></a>Exemple

La classe suivante pour un contrôle Calendar utilise l' `ISpecifyPropertyPages` interface pour indiquer aux conteneurs que ses propriétés peuvent être définies à l’aide d’une page de dates personnalisée et de la page de couleur de stock.

[!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]

## <a name="see-also"></a>Voir aussi

[Pages de propriétés](../atl/atl-com-property-pages.md)<br/>
[Exemple ATLPages](../overview/visual-cpp-samples.md)
