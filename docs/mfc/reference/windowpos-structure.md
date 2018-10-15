---
title: WINDOWPOS, Structure | Microsoft Docs
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
ms.openlocfilehash: 36e640187a87f3776a67a072e2fe77c141ed23f0
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334538"
---
# <a name="windowpos-structure"></a>WINDOWPOS, structure

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

*HWND*<br/>
Identifie la fenêtre.

*hwndInsertAfter*<br/>
Identifie la fenêtre derrière laquelle cette fenêtre est placée.

*x*<br/>
Spécifie la position du bord gauche de la fenêtre.

*y*<br/>
Spécifie la position du bord droit de la fenêtre.

*CX*<br/>
Spécifie la largeur de la fenêtre, en pixels.

*CY*<br/>
Spécifie la hauteur de la fenêtre, en pixels.

*flags*<br/>
Spécifie les options de positionnement de fenêtre. Ce membre peut être une des valeurs suivantes :

- SWP_DRAWFRAME Dessine un frame (défini dans la description de la classe de la fenêtre) autour de la fenêtre. La fenêtre reçoit un message WM_NCCALCSIZE.

- SWP_FRAMECHANGED envoie un WM_NCCALCSIZE du message à la fenêtre, même si la taille de la fenêtre n’est pas en cours de modification. Si cet indicateur n’est pas spécifié, WM_NCCALCSIZE est envoyée uniquement lorsque la taille de la fenêtre est en cours de modification.

- SWP_HIDEWINDOW masque la fenêtre.

- SWP_NOACTIVATE ne s’active pas la fenêtre.

- SWP_NOCOPYBITS ignore tout le contenu de la zone cliente. Si cet indicateur n’est pas spécifié, le contenu valid de la zone cliente est enregistré et copié dans la zone cliente, une fois que la fenêtre est dimensionnée ou repositionnée.

- SWP_NOMOVE conserve la position actuelle (ignore le `x` et `y` membres).

- SWP_NOOWNERZORDER changent position de la fenêtre propriétaire dans l’ordre de plan.

- SWP_NOSIZE conserve la taille actuelle (ignore le `cx` et `cy` membres).

- Ne de SWP_NOREDRAW ne redessine pas les modifications.

- SWP_NOREPOSITION identique à SWP_NOOWNERZORDER.

- SWP_NOSENDCHANGING empêche la fenêtre de réception du message WM_WINDOWPOSCHANGING.

- SWP_NOZORDER conserve le classement actuel (ignore le `hwndInsertAfter` membre).

- SWP_SHOWWINDOW affiche la fenêtre.

## <a name="requirements"></a>Configuration requise

**En-tête :** winuser.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

