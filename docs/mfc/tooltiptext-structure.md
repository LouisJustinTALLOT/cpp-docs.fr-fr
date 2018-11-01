---
title: TOOLTIPTEXT, structure
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: d184b1d507579309051cd6c70ea6525463c44881
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676510"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT, structure

Écrit votre [Gestionnaire de notification d’info-bulle outil](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), vous devez utiliser le **TOOLTIPTEXT** structure. Les membres de la **TOOLTIPTEXT** structure sont :

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
Identifie l’outil qui a besoin de texte. Le seul membre de cette structure, que vous devrez peut-être est l’ID de commande. du contrôle ID de commande du contrôle sera dans le *idFrom* membre de la **NMHDR** structure, accédé avec la syntaxe `hdr.idFrom`. Consultez [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) pour une description des membres de la **NMHDR** structure.

*lpszText*<br/>
Adresse d’une chaîne qui recevra le texte pour un outil.

*szText*<br/>
Mémoire tampon qui reçoit le texte info-bulle. Une application peut copier le texte à cette mémoire tampon comme alternative à la spécification d’une adresse de la chaîne.

*HINST*<br/>
Handle de l’instance qui contient une chaîne à utiliser en tant que le texte info-bulle. Si *lpszText* est l’adresse du texte info-bulle, ce membre a la valeur NULL.

Lorsque vous gérez le `TTN_NEEDTEXT` notification de message, spécifiez la chaîne à afficher dans une des manières suivantes :

- Copiez le texte dans la mémoire tampon spécifiée par le *szText* membre.

- Copiez l’adresse de la mémoire tampon qui contient le texte à la *lpszText* membre.

- Copiez l’identificateur de ressource de chaîne à la *lpszText* membre et copie le handle de l’instance qui contient la ressource à la *hinst* membre.

## <a name="see-also"></a>Voir aussi

[Info-bulles dans les fenêtres non dérivées de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

