---
title: CREATESTRUCT, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CREATESTRUCT
dev_langs:
- C++
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7bc510f0d0cfc88476c9e222f51bcfeb958e31a
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078465"
---
# <a name="createstruct-structure"></a>CREATESTRUCT, structure
Le `CREATESTRUCT` structure définit les paramètres d’initialisation passés à la procédure de fenêtre d’une application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagCREATESTRUCT {  
    LPVOID lpCreateParams;  
    HANDLE hInstance;  
    HMENU hMenu;  
    HWND hwndParent;  
    int cy;  
    int cx;  
    int y;  
    int x;  
    LONG style;  
    LPCSTR lpszName;  
    LPCSTR lpszClass;  
    DWORD dwExStyle;  
} CREATESTRUCT;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *lpCreateParams*  
 Points de données à utiliser pour créer la fenêtre.  
  
 *hInstance*  
 Identifie le handle d’instance du module du module qui possède la nouvelle fenêtre.  
  
 *hMenu*  
 Identifie le menu pour être utilisé par la nouvelle fenêtre. Si une fenêtre enfant, contient l’ID d’entier.  
  
 *hwndParent*  
 Identifie la fenêtre propriétaire de la nouvelle fenêtre. Ce membre est **NULL** si la nouvelle fenêtre est une fenêtre de niveau supérieur.  
  
 *CY*  
 Spécifie la hauteur de la nouvelle fenêtre.  
  
 *CX*  
 Spécifie la largeur de la nouvelle fenêtre.  
  
 *y*  
 Spécifie la coordonnée y de l’angle supérieur gauche de la nouvelle fenêtre. Coordonnées sont exprimées par rapport à la fenêtre parente si la nouvelle fenêtre est une fenêtre enfant ; Sinon, les coordonnées sont par rapport à l’origine de l’écran.  
  
 *x*  
 Spécifie la coordonnée x de l’angle supérieur gauche de la nouvelle fenêtre. Coordonnées sont exprimées par rapport à la fenêtre parente si la nouvelle fenêtre est une fenêtre enfant ; Sinon, les coordonnées sont par rapport à l’origine de l’écran.  
  
 *style*  
 Spécifie la nouvelle fenêtre [style](../../mfc/reference/styles-used-by-mfc.md).  
  
 *Caractère*  
 Pointe vers une chaîne se terminant par null qui spécifie le nom de la nouvelle fenêtre.  
  
 *lpszClass*  
 Pointe vers une chaîne se terminant par null qui spécifie le nom de la classe de la nouvelle fenêtre Windows (un [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) structure ; pour plus d’informations, consultez le Kit de développement).  
  
 *dwExStyle*  
 Spécifie le [style étendu](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) pour la nouvelle fenêtre.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


