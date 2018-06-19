---
title: Minmaxinfo, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MINMAXINFO
dev_langs:
- C++
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12161938f96e5044ae48f9eb5cf380fbc3840d3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369516"
---
# <a name="minmaxinfo-structure"></a>MINMAXINFO, structure
Le `MINMAXINFO` structure contient des informations sur la taille agrandie d’une fenêtre et position et sa taille minimale et maximale de suivi.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagMINMAXINFO {  
    POINT ptReserved;  
    POINT ptMaxSize;  
    POINT ptMaxPosition;  
    POINT ptMinTrackSize;  
    POINT ptMaxTrackSize;  
} MINMAXINFO;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ptReserved*  
 Réservé à un usage interne.  
  
 *ptMaxSize*  
 Spécifie la largeur agrandie (point.x) et la hauteur agrandie (point.y) de la fenêtre.  
  
 `ptMaxPosition`  
 Spécifie la position du côté gauche de la fenêtre agrandie (point.x) et la position du bord supérieur de la fenêtre agrandie (point.y).  
  
 *ptMinTrackSize*  
 Spécifie la largeur (point.x) de suivi minimale et la hauteur (point.y) de la fenêtre de suivi minimale.  
  
 *ptMaxTrackSize*  
 Spécifie le nombre maximal (point.x) de largeur de suivi et la valeur maximale (point.y) de hauteur de la fenêtre de suivi.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

