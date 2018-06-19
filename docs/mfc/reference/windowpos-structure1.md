---
title: WINDOWPOS Structure1 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4abd236998f37f0d719f41827d05a17fde56fde
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379292"
---
# <a name="windowpos-structure1"></a>WINDOWPOS Structure1
Le `WINDOWPOS` structure contient des informations sur la taille et la position d’une fenêtre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagWINDOWPOS { /* wp */  
    HWND hwnd;  
    HWND hwndInsertAfter;  
    int x;  
    int y;  
    int cx;  
    int cy;  
    UINT flags;  
} WINDOWPOS;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *HWND*  
 Identifie la fenêtre.  
  
 *hwndInsertAfter*  
 Identifie la fenêtre derrière laquelle cette fenêtre est placée.  
  
 *x*  
 Spécifie la position du bord gauche de la fenêtre.  
  
 *y*  
 Spécifie la position du bord droit de la fenêtre.  
  
 `cx`  
 Spécifie la largeur de la fenêtre, en pixels.  
  
 `cy`  
 Spécifie la hauteur de la fenêtre, en pixels.  
  
 `flags`  
 Spécifie les options de positionnement de fenêtre. Ce membre peut être une des valeurs suivantes :  
  
- **SWP_DRAWFRAME** Dessine une image (définie dans la description de la classe de la fenêtre) autour de la fenêtre. La fenêtre reçoit un `WM_NCCALCSIZE` message.  
  
- **SWP_FRAMECHANGED** envoie un `WM_NCCALCSIZE` de message à la fenêtre, même si la taille de la fenêtre n’est pas modifiée. Si cet indicateur n’est pas spécifié, `WM_NCCALCSIZE` est envoyée uniquement lorsque la taille de la fenêtre est modifiée.  
  
- **SWP_HIDEWINDOW** masque la fenêtre.  
  
- `SWP_NOACTIVATE` N’active pas la fenêtre.  
  
- **SWP_NOCOPYBITS** ignore tout le contenu de la zone cliente. Si cet indicateur n’est pas spécifié, le contenu valid de la zone cliente est enregistré et copié dans la zone cliente une fois que la fenêtre est dimensionnée ou repositionnée.  
  
- `SWP_NOMOVE` Conserve la position actuelle (ignore le **x** et **y** membres).  
  
- **SWP_NOOWNERZORDER** ne modifie pas la position de la fenêtre propriétaire dans l’ordre de plan.  
  
- `SWP_NOSIZE` Conserve la taille actuelle (ignore le **cx** et **cy** membres).  
  
- **SWP_NOREDRAW** ne redessine pas les modifications.  
  
- **SWP_NOREPOSITION** identique **SWP_NOOWNERZORDER**.  
  
- **SWP_NOSENDCHANGING** empêche la fenêtre de réception le `WM_WINDOWPOSCHANGING` message.  
  
- `SWP_NOZORDER` Conserve le classement actuel (ignore le **hwndInsertAfter** membre).  
  
- **SWP_SHOWWINDOW** affiche la fenêtre.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

