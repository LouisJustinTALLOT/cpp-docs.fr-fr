---
title: Feuilles de propriétés et Pages de propriétés dans MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a54469672c67e43d3692bc47d0b3efa00c18f8f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348604"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Pages et feuilles de propriétés dans MFC
Une feuille de propriétés, également connu sous une onglet boîte de dialogue, est une boîte de dialogue qui contient les pages de propriétés. Chaque page de propriétés est basé sur une ressource de modèle de boîte de dialogue et contient des contrôles. Il est placé sur une page avec un onglet en haut. L’onglet Nom de la page et indique sa finalité. Les utilisateurs cliquent sur un onglet dans la feuille de propriétés pour sélectionner un ensemble de contrôles.  
  
 Utilisez les pages pour regrouper les contrôles dans la feuille de propriétés en groupes cohérents. La feuille de propriétés de relation contenant-contenu a généralement plusieurs contrôles qui lui sont propres. Elles s’appliquent à toutes les pages.  
  
 Feuilles de propriétés sont basés sur la classe [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Pages de propriétés sont basés sur la classe [CPropertyPage](../mfc/reference/cpropertypage-class.md).  
  
 Une feuille de propriétés est un type spécial de la boîte de dialogue qui est généralement utilisé pour modifier les attributs d’un objet externe, telles que la sélection actuelle dans une vue. La feuille de propriétés possède trois parties principales : la boîte de dialogue contenant des pages de propriétés d’un ou plusieurs affichent une à la fois et qu’un onglet en haut de chaque page de l’utilisateur clique pour sélectionner cette page. Feuilles de propriétés sont utiles pour les cas où vous disposez de plusieurs groupes similaires de paramètres ou options à modifier. Une feuille de propriétés regroupe les informations d’une façon facilement compréhensible.  
  
> [!NOTE]
>  Lorsque vous essayez d’afficher une feuille de propriétés à l’aide de `CPropertySheet::DoModal`, le système peut générer une exception de première chance. Cette exception se produit parce que le système tente de modifier le [Styles de fenêtre](../mfc/reference/styles-used-by-mfc.md#window-styles) de l’objet avant de l’objet a été créé. Pour plus d’informations sur cette exception et également comment éviter ou à gérer, consultez [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).  
  
## <a name="see-also"></a>Voir aussi  
 [Feuilles de propriétés](../mfc/property-sheets-mfc.md)

