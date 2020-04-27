---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: 65a8ce08e4f8606f168b101aa4daba23ef541051
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168668"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler`nom de la fonction identifiée par le deuxième paramètre de la macro MESSAGE_HANDLER dans votre table des messages.

## <a name="syntax"></a>Syntaxe

```cpp
LRESULT MessageHandler(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Paramètres

*uMsg*<br/>
Spécifie le message.

*wParam*<br/>
Informations supplémentaires spécifiques au message.

*lParam*<br/>
Informations supplémentaires spécifiques au message.

*bHandled*<br/>
La table des messages affecte à *bHandled* la `MessageHandler` valeur true avant l’appel à. Si `MessageHandler` ne gère pas complètement le message, il doit affecter à *BHANDLED* la valeur false pour indiquer que le message doit être traité ultérieurement.

## <a name="return-value"></a>Valeur de retour

Résultat du traitement du message. 0 en cas de réussite.

## <a name="remarks"></a>Notes

Pour obtenir un exemple d’utilisation de ce gestionnaire de messages dans une table des messages, consultez [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)<br/>
[Tables des messages](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
