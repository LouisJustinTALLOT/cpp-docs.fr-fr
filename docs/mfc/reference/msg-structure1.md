---
title: MSG Structure1 | Documents Microsoft
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
ms.openlocfilehash: 41dbbcdd3404705a9ac7c6c7969a9ebeeb0238f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372255"
---
# <a name="msg-structure1"></a>MSG Structure1
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
 Identifie la fenêtre dont procédure de fenêtre reçoit le message.  
  
 `message`  
 Spécifie le numéro du message.  
  
 `wParam`  
 Spécifie des informations supplémentaires sur le message. La signification exacte dépend de la valeur de la **message** membre.  
  
 `lParam`  
 Spécifie des informations supplémentaires sur le message. La signification exacte dépend de la valeur de la **message** membre.  
  
 `time`  
 Spécifie l’heure à laquelle le message a été publié.  
  
 `pt`  
 Spécifie la position du curseur, en coordonnées d’écran, lorsque le message a été publié.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

