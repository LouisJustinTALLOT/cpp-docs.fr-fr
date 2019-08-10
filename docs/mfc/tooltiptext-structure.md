---
title: TOOLTIPTEXT, structure
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: 2eb899e66acbadbe45aae2c8adbb356bf4730191
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915248"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT, structure

Lors de l’écriture de votre gestionnaire de notifications d' [info-bulle](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), vous devez utiliser la structure **ToolTipText** . Les membres de la structure **ToolTipText** sont:

```cpp
typedef struct {
    NMHDR     hdr;        // required for all WM_NOTIFY messages
    LPTSTR    lpszText;   // see below
    TCHAR     szText[80]; // buffer for tool tip text
    HINSTANCE hinst;      // see below
    UINT      uflags;     // flag indicating how to interpret the
                          // idFrom member of the NMHDR structure
                          // that is included in the structure
} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;
```

*hdr*<br/>
Identifie l’outil qui a besoin de texte. Le seul membre de cette structure dont vous pouvez avoir besoin est l’ID de commande du contrôle. L’ID de commande du contrôle se trouve dans le membre *idFrom* de la structure **NMHDR** , accessible à l' `hdr.idFrom`aide de la syntaxe. Consultez [NMHDR](/windows/desktop/api/richedit/ns-richedit-nmhdr) pour une discussion sur les membres de la structure **NMHDR** .

*lpszText*<br/>
Adresse d’une chaîne devant recevoir le texte d’un outil.

*szText*<br/>
Mémoire tampon qui reçoit le texte d’info-bulle. Une application peut copier le texte dans cette mémoire tampon en guise d’alternative à la spécification d’une adresse de chaîne.

*hinst*<br/>
Handle de l’instance qui contient une chaîne à utiliser comme texte d’info-bulle. Si *lpszText* est l’adresse du texte d’info-bulle, ce membre est null.

Lorsque vous gérez le `TTN_NEEDTEXT` message de notification, spécifiez la chaîne à afficher de l’une des manières suivantes:

- Copiez le texte dans la mémoire tampon spécifiée par le membre *szText* .

- Copiez l’adresse de la mémoire tampon qui contient le texte dans le membre *lpszText* .

- Copiez l’identificateur d’une ressource de type chaîne dans le membre *lpszText* et copiez le handle de l’instance qui contient la ressource dans le membre *HINST* .

## <a name="see-also"></a>Voir aussi

[Info-bulles dans les fenêtres non dérivées de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
