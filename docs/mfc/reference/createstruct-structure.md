---
title: CREATESTRUCT, Structure | Microsoft Docs
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
ms.openlocfilehash: 6036490b21ccbd86dfed56ea90226cbb2db8d596
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848468"
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
 Identifie le handle d’instance de module du module qui possède la nouvelle fenêtre.  
  
 *hMenu*  
 Identifie le menu pour être utilisé par la nouvelle fenêtre. Si une fenêtre enfant, contient l’ID d’entier.  
  
 *hwndParent*  
 Identifie la fenêtre propriétaire de la nouvelle fenêtre. Ce membre a la valeur NULL si la nouvelle fenêtre est une fenêtre de niveau supérieur.  
  
 *CY*  
 Spécifie la hauteur de la nouvelle fenêtre.  
  
 *CX*  
 Spécifie la largeur de la nouvelle fenêtre.  
  
 *y*  
 Spécifie la coordonnée y du coin supérieur gauche de la nouvelle fenêtre. Coordonnées sont exprimées par rapport à la fenêtre parente si la nouvelle fenêtre est une fenêtre enfant ; Sinon, les coordonnées sont relatif à l’origine de l’écran.  
  
 *x*  
 Spécifie la coordonnée x du coin supérieur gauche de la nouvelle fenêtre. Coordonnées sont exprimées par rapport à la fenêtre parente si la nouvelle fenêtre est une fenêtre enfant ; Sinon, les coordonnées sont relatif à l’origine de l’écran.  
  
 *style*  
 Spécifie la nouvelle fenêtre [style](../../mfc/reference/styles-used-by-mfc.md).  
  
 *Caractère*  
 Pointe vers une chaîne se terminant par null qui spécifie le nom de la nouvelle fenêtre.  
  
 *lpszClass*  
 Pointe vers une chaîne se terminant par null qui spécifie le nom de la classe de la nouvelle fenêtre Windows (un [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) structure ; pour plus d’informations, consultez le Kit de développement logiciel Windows).  
  
 *dwExStyle*  
 Spécifie le [style étendu](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) pour la nouvelle fenêtre.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


