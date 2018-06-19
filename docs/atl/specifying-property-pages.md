---
title: Spécification des Pages de propriétés (ATL) | Documents Microsoft
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
ms.openlocfilehash: e8d4cbeaa8ea9a57f9287f2d2fe78c61884ba4a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358923"
---
# <a name="specifying-property-pages"></a>Spécification des Pages de propriétés
Lorsque vous créez un contrôle ActiveX, vous souhaitez souvent associer à des pages de propriétés qui peuvent être utilisés pour définir les propriétés de votre contrôle. Contrôle l’utilisation de conteneurs le **ISpecifyPropertyPages** interface pour découvrir les pages de propriétés peuvent être utilisés pour définir les propriétés de votre contrôle. Vous devez implémenter cette interface sur votre contrôle.  
  
 Pour implémenter **ISpecifyPropertyPages** à l’aide d’ATL, procédez comme suit :  
  
1.  Dérivez votre classe de [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md).  
  
2.  Ajoutez une entrée pour **ISpecifyPropertyPages** mappage COM de votre classe.  
  
3.  Ajouter un [PROP_PAGE](reference/property-map-macros.md#prop_page) entrée pour le mappage de propriété pour chaque page associée à votre contrôle.  
  
> [!NOTE]
>  Lors de la génération d’un contrôle standard à l’aide de la [Assistant contrôle ATL](../atl/reference/atl-control-wizard.md), vous devez uniquement ajouter les `PROP_PAGE` entrées au mappage de propriété. L’Assistant génère le code nécessaire pour les autres étapes.  
  
 Les conteneurs valides affichent les pages de propriétés spécifié dans le même ordre que les `PROP_PAGE` entrées dans le mappage de propriété. En règle générale, vous devez placer les entrées de pages de propriété standard après les entrées des pages personnalisées dans le mappage de propriété, afin que les utilisateurs voient les pages spécifiques à votre contrôle tout d’abord.  
  
## <a name="example"></a>Exemple  
 La classe suivante d’un calendrier de contrôles utilise la **ISpecifyPropertyPages** interface pour signaler aux conteneurs que ses propriétés peuvent être définies à l’aide d’une page de date personnalisée et la page stock de couleurs.  
  
 [!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]  
  
## <a name="see-also"></a>Voir aussi  
 [Pages de propriétés](../atl/atl-com-property-pages.md)   
 [Exemple ATLPages](../visual-cpp-samples.md)

