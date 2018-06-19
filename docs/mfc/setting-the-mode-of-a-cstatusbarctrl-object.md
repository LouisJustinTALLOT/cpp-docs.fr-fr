---
title: Définition du Mode d’un objet CStatusBarCtrl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d875f2b93309e96bc3d612a8adc55b5af387026
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380917"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Définition du mode d'un objet CStatusBarCtrl
Il existe deux modes pour un `CStatusBarCtrl` objet : simple et non simple. Dans la plupart des cas, votre contrôle de barre d’état aura une ou plusieurs parties, ainsi que le texte et éventuellement une icône ou des icônes. Il s’agit du mode simple. Pour plus d’informations sur ce mode, consultez [initialisation des parties d’un objet CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).  
  
 Toutefois, il existe des cas où vous devez uniquement afficher une seule ligne de texte. Dans ce cas, le mode simple suffit à vos besoins. Pour modifier le mode de la `CStatusBarCtrl` objet simple, effectuez un appel à la [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) fonction membre. Une fois que le contrôle de barre d’état est en mode simple, définissez le texte en appelant le **SetText** fonction membre, en passant 255 comme valeur pour le **nPane** paramètre.  
  
 Vous pouvez utiliser la [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) afin de déterminer dans quel mode le `CStatusBarCtrl` objet se trouve dans.  
  
> [!NOTE]
>  Si l’objet de barre d’état est en cours de modification d’état simple, ou vice versa, la fenêtre est redessinée d’immédiatement et, le cas échéant, toutes les parties définies sont automatiquement restaurées.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

