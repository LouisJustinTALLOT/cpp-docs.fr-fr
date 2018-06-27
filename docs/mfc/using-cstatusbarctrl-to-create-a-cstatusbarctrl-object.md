---
title: Utilisation de CStatusBarCtrl pour créer un objet CStatusBarCtrl | Documents Microsoft
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
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb378bba1505f8bbc3739c070d52abe9ef4f8afc
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953823"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Utilisation de CStatusBarCtrl pour créer un objet CStatusBarCtrl
Voici un exemple d’utilisation classique de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):  
  
### <a name="to-use-a-status-bar-control-with-parts"></a>Pour utiliser un contrôle de barre d’état avec des parties  
  
1.  Construire la `CStatusBarCtrl` objet.  
  
2.  Appelez [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) si vous souhaitez définir la hauteur minimale du contrôle de barre d’état de zone de dessin.  
  
3.  Appelez [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) pour définir la couleur d’arrière-plan du contrôle de barre d’état.  
  
4.  Appelez [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) pour définir le nombre de parties dans un contrôle et les coordonnées du bord droit de chaque partie de la barre d’état.  
  
5.  Appelez [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) pour définir le texte d’une partie donnée du contrôle de barre d’état. Le message invalide la partie du contrôle qui a changé, provoquant l’affichage du nouveau texte lorsque le contrôle reçoit le message WM_PAINT.  
  
 Dans certains cas, la barre d’état doit afficher une ligne de texte. Dans ce cas, effectuez un appel à [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple). Cela place le contrôle de barre d’état en mode « simple », qui affiche une seule ligne de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

