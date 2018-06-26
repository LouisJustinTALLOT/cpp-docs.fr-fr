---
title: Gestion des Notifications de conseil outil | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8df4b584a4e8b0ef940d5934a5968037427c607d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931812"
---
# <a name="handling-tool-tip-notifications"></a>Gestion des notifications pour les info-bulles
Lorsque vous spécifiez la **TBSTYLE_TOOLTIPS** style, la barre d’outils crée et gère un contrôle info-bulle. Une info-bulle est une petite fenêtre contextuelle qui contient une ligne de texte décrivant un bouton de barre d’outils. L’info-bulle est cachée uniquement lorsque l’utilisateur place le curseur sur un bouton de barre d’outils et il quitte ensuite pendant environ une demi-seconde. L’info-bulle s’affiche près du curseur.  
  
 Avant de l’info-bulle s’affiche, le **TTN_NEEDTEXT** message de notification est envoyé à la fenêtre propriétaire de la barre d’outils pour récupérer le texte descriptif pour le bouton. Si la fenêtre propriétaire de la barre d’outils est un `CFrameWnd` fenêtre outil des conseils sont affichés sans effort supplémentaire, car `CFrameWnd` possède un gestionnaire par défaut pour le **TTN_NEEDTEXT** notification. Si la fenêtre propriétaire de la barre d’outils n’est pas dérivée de `CFrameWnd`, tel qu’une vue de formulaire ou de boîte de dialogue, vous devez ajouter une entrée dans la table des messages de votre fenêtre propriétaire et fournir un gestionnaire de notification dans la table des messages. L’entrée à la table des messages de votre fenêtre propriétaire est la suivante :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]  
  
## <a name="remarks"></a>Notes  
 `memberFxn`  
 La fonction membre à appeler lorsque le texte est nécessaire pour ce bouton.  
  
 Notez que l’id d’une info-bulle est toujours 0.  
  
 Outre la **TTN_NEEDTEXT** notification, un contrôle info-bulle peut envoyer les notifications suivantes à un contrôle de barre d’outils :  
  
|Notification|Signification|  
|------------------|-------------|  
|**TTN_NEEDTEXTA**|Contrôle info-bulle nécessite un texte ASCII (Windows 95 uniquement)|  
|**NOTIFICATIONS TTN_NEEDTEXTW**|Contrôle info-bulle nécessite un texte UNICODE (Windows NT uniquement)|  
|**TBN_HOTITEMCHANGE**|Indique que l’élément (en surbrillance) à chaud a changé.|  
|**NM_RCLICK**|Indique que l’utilisateur a cliqué un bouton.|  
|**TBN_DRAGOUT**|Indique que l’utilisateur a cliqué sur le bouton et déplacé le pointeur hors du bouton. Il permet à une application implémenter une opération glisser-déplacer à partir d’un bouton de barre d’outils. Lorsque vous recevez cette notification, l’application commence l’opération glisser et déplacer.|  
|**TBN_DROPDOWN**|Indique l’utilisateur a cliqué sur un bouton qui utilise le **TBSTYLE_DROPDOWN** style.|  
|**TBN_GETOBJECT**|Indique l’utilisateur a déplacé le pointeur sur un bouton qui utilise le **TBSTYLE_DROPPABLE** style.|  
  
 Pour un exemple de fonction de gestionnaire et plus d’informations sur l’activation des info-bulles, consultez [info-bulles](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

