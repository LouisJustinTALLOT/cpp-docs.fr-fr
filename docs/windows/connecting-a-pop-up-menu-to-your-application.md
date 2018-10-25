---
title: Connexion d’un Menu contextuel à votre Application C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- menus [C++], pop-up
- shortcut menus [C++], connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 643e758d063744c155ff3e03a2ff8d6bede78822
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075149"
---
# <a name="connecting-a-pop-up-menu-to-your-c-application"></a>Connexion d’un Menu contextuel à votre Application C++

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>Pour connecter un menu contextuel à votre application

1. Ajoutez un gestionnaire de messages pour WM_CONTEXTMENU (par exemple). Pour plus d’informations, consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).

2. Ajoutez le code suivant au gestionnaire de messages :

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > Le [CPoint](../atl-mfc-shared/reference/cpoint-class.md) passé par le message gestionnaire est en coordonnées d’écran.

## <a name="requirements"></a>Configuration requise

MFC

## <a name="see-also"></a>Voir aussi

[Création de menus contextuels](../windows/creating-pop-up-menus.md)<br/>
[Éditeur de menus](../windows/menu-editor.md)