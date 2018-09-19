---
title: RECT, Structure1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e71459a1c22b9295c5c88ce29da9e494660fa26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046301"
---
# <a name="rect-structure1"></a>RECT, Structure1
Le `RECT` structure définit les coordonnées des angles supérieur gauche et inférieur droit d’un rectangle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagRECT {  
    LONG left;  
    LONG top;  
    LONG right;  
    LONG bottom;  
} RECT;  
```  
  
## <a name="members"></a>Membres  
`left`<br/>
Spécifie la coordonnée x du coin supérieur gauche d’un rectangle.  
  
`top`<br/>
Spécifie la coordonnée y du coin supérieur gauche d’un rectangle.  
  
`right`<br/>
Spécifie la coordonnée x du coin inférieur droit d’un rectangle.  
  
`bottom`<br/>
Spécifie la coordonnée y du coin inférieur droit d’un rectangle.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** windef.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect, classe](../../atl-mfc-shared/reference/crect-class.md)
