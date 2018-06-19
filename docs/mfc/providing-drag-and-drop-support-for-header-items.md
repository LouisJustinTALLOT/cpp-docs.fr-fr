---
title: Prise en charge du glisser-déplacer pour les éléments d’en-tête | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50cd19d4828269d0591afd0b46768e9917b96906
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349342"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Prise en charge du glisser-déposer pour les éléments d’en-tête
Pour fournir la prise en charge du glisser-déplacer pour les éléments d’en-tête, spécifiez la `HDS_DRAGDROP` style. Prise en charge du glisser-déplacer pour les éléments d’en-tête donne à l’utilisateur la possibilité de réorganiser les éléments d’un contrôle header. Le comportement par défaut fournit une image translucide de l’élément d’en-tête déplacé et un indicateur visuel de la nouvelle position, si l’élément d’en-tête est supprimée.  
  
 Comme avec les fonctionnalités communes de glisser-déplacer, vous pouvez étendre le comportement de glisser-déplacer par défaut en gérant la **standard** et **HDN_ENDDRAG** des notifications. Vous pouvez également personnaliser l’apparence de l’image glisser en substituant le [fonction membre CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) fonction membre.  
  
> [!NOTE]
>  Si vous fournissez la prise en charge du glisser-déplacer pour un contrôle header incorporé dans un contrôle de liste, consultez la section Styles étendus dans le [la modification des Styles de contrôle liste](../mfc/changing-list-control-styles.md) rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)

