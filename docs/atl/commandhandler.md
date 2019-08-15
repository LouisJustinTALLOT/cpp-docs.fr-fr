---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 99a95228f6036e5f391395be367cdef39ca3dc3b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492452"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler`est la fonction identifiée par le troisième paramètre de la macro COMMAND_HANDLER dans votre table des messages.

## <a name="syntax"></a>Syntaxe

```cpp
LRESULT CommandHandler(
    WORD wNotifyCode,
    WORD wID,
    HWND hWndCtl,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Paramètres

*wNotifyCode*<br/>
Code de notification.

*wID*<br/>
Identificateur de l’élément de menu, du contrôle ou de l’accélérateur.

*hWndCtl*<br/>
Handle d’un contrôle de fenêtre.

*bHandled*<br/>
La table des messages affecte à *bHandled* la `CommandHandler` valeur true avant l’appel à. Si `CommandHandler` ne gère pas complètement le message, il doit affecter à *bHandled* la valeur false pour indiquer que le message doit être traité ultérieurement.

## <a name="return-value"></a>Valeur de retour

Résultat du traitement du message. 0 en cas de réussite.

## <a name="remarks"></a>Notes

Pour obtenir un exemple d’utilisation de ce gestionnaire de messages dans une table des messages, consultez [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)<br/>
[Tables des messages](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
