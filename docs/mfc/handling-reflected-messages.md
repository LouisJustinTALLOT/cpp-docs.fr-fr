---
title: Gestion des Messages réfléchis | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05b5f62169d2b65010ec75ab8c8b5c30959b77b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348974"
---
# <a name="handling-reflected-messages"></a>Gestion des messages réfléchis
Message réflexion vous permet de gérer les messages pour un contrôle, tel que `WM_CTLCOLOR`, **WM_COMMAND**, et **WM_NOTIFY**, dans le contrôle lui-même. Cela rend le contrôle plus autonome et portable. Le mécanisme fonctionne avec les contrôles communs Windows ainsi qu’avec les contrôles ActiveX (anciennement appelés contrôles OLE).  
  
 Message réflexion vous permet de réutiliser vos `CWnd`-plus facilement les classes dérivées. Fonctionnement par le biais de la réflexion de message [CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify), à l’aide de spécial **ON_XXX_REFLECT** les entrées de mappage de message : par exemple, **ON_CTLCOLOR_REFLECT** et **ON_CONTROL_REFLECT**. [Technical Note 62](../mfc/tn062-message-reflection-for-windows-controls.md) explique la réflexion de message plus en détail.  
  
## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi  
  
-   [En savoir plus sur la réflexion de message](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [Implémenter le renvoi de message pour un contrôle commun](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [Implémenter le renvoi de message pour un contrôle ActiveX](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Déclaration des fonctions de gestionnaire de messages](../mfc/declaring-message-handler-functions.md)
