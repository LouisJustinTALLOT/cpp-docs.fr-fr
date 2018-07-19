---
title: PAINTSTRUCT, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- PAINTSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75a3db6c6beb18afe2303b464fcab290b2e132fc
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338208"
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT, structure
Le `PAINTSTRUCT` structure contient des informations qui peuvent être utilisées pour peindre la zone cliente d’une fenêtre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagPAINTSTRUCT {  
    HDC hdc;  
    BOOL fErase;  
    RECT rcPaint;  
    BOOL fRestore;  
    BOOL fIncUpdate;  
    BYTE rgbReserved[16];  
} PAINTSTRUCT;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *HDC*  
 Identifie le contexte d’affichage à utiliser pour peindre.  
  
 *fErase*  
 Spécifie si l’arrière-plan doit être redessiné. Il n’est pas 0 si l’application doit redessiner l’arrière-plan. L’application est responsable du dessin de l’arrière-plan si une classe de fenêtre Windows est créée sans un pinceau d’arrière-plan (consultez la description de la `hbrBackground` membre de la [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) structure dans le SDK Windows).  
  
 *rcPaint*  
 Spécifie l’angle supérieur gauche et inférieure droite du rectangle dans lequel la peinture est demandée.  
  
 *fRestore*  
 Membre réservé. Il est utilisé en interne par Windows.  
  
 *fIncUpdate*  
 Membre réservé. Il est utilisé en interne par Windows.  
  
 *rgbReserved [16]*  
 Membre réservé. Un bloc de mémoire utilisée en interne par Windows réservé.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

