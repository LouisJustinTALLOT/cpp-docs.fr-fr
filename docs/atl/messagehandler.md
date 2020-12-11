---
description: 'En savoir plus sur : MessageHandler'
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: d369b94721e57eb4adc704570bc09d1aae184fe1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159503"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler` nom de la fonction identifiée par le deuxième paramètre de la macro MESSAGE_HANDLER dans votre table des messages.

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
La table des messages affecte à *bHandled* la valeur true avant l' `MessageHandler` appel à. Si `MessageHandler` ne gère pas complètement le message, il doit affecter à *bHandled* la valeur false pour indiquer que le message doit être traité ultérieurement.

## <a name="return-value"></a>Valeur renvoyée

Résultat du traitement du message. 0 en cas de réussite.

## <a name="remarks"></a>Notes

Pour obtenir un exemple d’utilisation de ce gestionnaire de messages dans une table des messages, consultez [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)<br/>
[Tables des messages](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
