---
title: Nccalcsize_params, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 095b66af9dab08e3d8fad040c43e2eaf8d2beb81
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335641"
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS, structure
Le `NCCALCSIZE_PARAMS` structure contient des informations qu’une application peut utiliser lors du traitement du message WM_NCCALCSIZE pour calculer la taille, la position et le contenu valid de la zone cliente d’une fenêtre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *rgrc*  
 Spécifie un tableau de rectangles. Le premier contient les nouvelles coordonnées d’une fenêtre qui a été déplacé ou redimensionné. Le deuxième contient les coordonnées de la fenêtre avant qu’elle a été déplacée ou redimensionnée. Le troisième contient les coordonnées de la zone cliente d’une fenêtre avant qu’elle a été déplacée ou redimensionnée. Si la fenêtre est une fenêtre enfant, les coordonnées sont relatives à la zone client de la fenêtre parente. Si la fenêtre est une fenêtre de niveau supérieur, les coordonnées sont par rapport à l’écran.  
  
 *lppos*  
 Pointe vers un [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) structure qui contient les valeurs de taille et la position spécifiées dans l’opération qui a provoqué la fenêtre à être déplacé ou redimensionné.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

