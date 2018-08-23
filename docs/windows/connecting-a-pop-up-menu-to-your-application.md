---
title: Connexion d’un Menu contextuel à votre Application | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pop-up menus, connecting to applications
- context menus, connecting to applications
- menus, pop-up
- shortcut menus, connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce7a8d53c56e6a17d5ef57222bab725a4addf8fd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42581155"
---
# <a name="connecting-a-pop-up-menu-to-your-application"></a>Connexion d'un menu contextuel à votre application

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

[Création de menus contextuels](../windows/creating-pop-up-menus.md)  
[Éditeur de menus](../windows/menu-editor.md)  