---
title: MSG, Structure1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe629c2f279b6b258f4824229490f7b72b4ce4d
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338810"
---
# <a name="msg-structure1"></a>MSG, Structure1
Le `MSG` structure contient des informations de message à partir de la file d’attente des messages d’un thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagMSG {     // msg    
    HWND hwnd;  
    UINT message;  
    WPARAM wParam;  
    LPARAM lParam;  
    DWORD time;  
    POINT pt;  
} MSG;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *HWND*  
 Identifie la fenêtre dont la procédure de fenêtre reçoit le message.  
  
 *message*  
 Spécifie le numéro du message.  
  
 *wParam*  
 Spécifie des informations supplémentaires sur le message. La signification exacte dépend de la valeur de la `message` membre.  
  
 *lParam*  
 Spécifie des informations supplémentaires sur le message. La signification exacte dépend de la valeur de la `message` membre.  
  
 *time*  
 Spécifie l’heure à laquelle le message a été publié.  
  
 *pt*  
 Spécifie la position du curseur, en coordonnées d’écran, lorsque le message a été publié.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

