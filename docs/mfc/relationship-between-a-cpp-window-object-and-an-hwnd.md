---
title: Relation entre un objet fenêtre C++ et un HWND
ms.date: 11/19/2018
f1_keywords:
- HWND
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
ms.openlocfilehash: fcd885fbaf7e81d68bcd51edc4b74c553f70578b
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176859"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Relation entre un objet fenêtre C++ et un HWND

La fenêtre *objet* est un objet du C++ `CWnd` classe (ou une classe dérivée) que votre programme crée directement. Il va et vient en réponse aux appels de constructeur et destructeur de votre programme. Le Windows *fenêtre*, quant à eux, est un handle opaque à une structure de données Windows interne qui correspond à une fenêtre et consomme des ressources système lorsqu’il est présent. Une fenêtre Windows est identifiée par un handle de fenêtre « » (`HWND`) et est créé après le `CWnd` objet est créé par un appel à la `Create` fonction membre de classe `CWnd`. La fenêtre peut être détruite par un appel de programme ou par l’action d’un utilisateur. Le handle de fenêtre est stocké dans l’objet de fenêtre *m_hWnd* variable membre. La figure suivante montre la relation entre l’objet fenêtre C++ et la fenêtre de Windows. Création de fenêtres est abordée dans [Windows création](../mfc/creating-windows.md). Détruire des fenêtres est abordée dans [destruction d’objets](../mfc/destroying-window-objects.md).

![CWnd objet fenêtre et fenêtre résultante](../mfc/media/vc37fj1.gif "CWnd objet fenêtre et fenêtre résultante") <br/>
Objet de fenêtre et de la fenêtre de Windows

## <a name="see-also"></a>Voir aussi

[Objets fenêtre](../mfc/window-objects.md)
