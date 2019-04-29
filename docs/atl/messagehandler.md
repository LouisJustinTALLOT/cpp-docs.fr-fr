---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: 1acd56357f9ce234e3c479fd8fa88c1ed8407878
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261694"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler` est le nom de la fonction identifiée par le deuxième paramètre de la macro MESSAGE_HANDLER dans votre table des messages.

## <a name="syntax"></a>Syntaxe

```
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
Les jeux de mappage de message *bHandled* sur TRUE avant `MessageHandler` est appelée. Si `MessageHandler` ne gère pas entièrement le message, il doit définir *bHandled* sur FALSE pour indiquer que le message nécessite un traitement supplémentaire.

## <a name="return-value"></a>Valeur de retour

Le résultat du traitement de message. 0 si l’opération réussit.

## <a name="remarks"></a>Notes

Pour obtenir un exemple de l’utilisation de ce gestionnaire de messages dans une table des messages, consultez [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)<br/>
[Tables des messages](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
