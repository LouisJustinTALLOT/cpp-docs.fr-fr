---
title: CREATESTRUCT, structure
ms.date: 11/04/2016
f1_keywords:
- CREATESTRUCT
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
ms.openlocfilehash: 13f715dc914ccc052945790aeaff9c47bd34ed46
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619646"
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

*lpCreateParams*<br/>
Points de données à utiliser pour créer la fenêtre.

*hInstance*<br/>
Identifie le handle d’instance de module du module qui possède la nouvelle fenêtre.

*hMenu*<br/>
Identifie le menu pour être utilisé par la nouvelle fenêtre. Si une fenêtre enfant, contient l’ID d’entier.

*hwndParent*<br/>
Identifie la fenêtre propriétaire de la nouvelle fenêtre. Ce membre a la valeur NULL si la nouvelle fenêtre est une fenêtre de niveau supérieur.

*CY*<br/>
Spécifie la hauteur de la nouvelle fenêtre.

*CX*<br/>
Spécifie la largeur de la nouvelle fenêtre.

*y*<br/>
Spécifie la coordonnée y du coin supérieur gauche de la nouvelle fenêtre. Coordonnées sont exprimées par rapport à la fenêtre parente si la nouvelle fenêtre est une fenêtre enfant ; Sinon, les coordonnées sont relatif à l’origine de l’écran.

*x*<br/>
Spécifie la coordonnée x du coin supérieur gauche de la nouvelle fenêtre. Coordonnées sont exprimées par rapport à la fenêtre parente si la nouvelle fenêtre est une fenêtre enfant ; Sinon, les coordonnées sont relatif à l’origine de l’écran.

*style*<br/>
Spécifie la nouvelle fenêtre [style](../../mfc/reference/styles-used-by-mfc.md).

*Caractère*<br/>
Pointe vers une chaîne se terminant par null qui spécifie le nom de la nouvelle fenêtre.

*lpszClass*<br/>
Pointe vers une chaîne se terminant par null qui spécifie le nom de la classe de la nouvelle fenêtre Windows (un [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) structure ; pour plus d’informations, consultez le Kit de développement logiciel Windows).

*dwExStyle*<br/>
Spécifie le [style étendu](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) pour la nouvelle fenêtre.

## <a name="requirements"></a>Configuration requise

**En-tête :** winuser.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)

