---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandHandler
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 8259dfe8ead608876b3637d1dca9c3e808bb419d
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694632"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler` la fonction est identifiée par le troisième paramètre de la macro COMMAND_HANDLER dans votre table des messages.

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
Le code de notification.

*wID*<br/>
L’identificateur de l’élément de menu, un contrôle ou un accélérateur.

*hWndCtl*<br/>
Handle vers un contrôle de fenêtre.

*bHandled*<br/>
Les jeux de mappage de message *bHandled* sur TRUE avant `CommandHandler` est appelée. Si `CommandHandler` ne gère pas entièrement le message, il doit définir *bHandled* sur FALSE pour indiquer que le message nécessite un traitement supplémentaire.

## <a name="return-value"></a>Valeur de retour

Le résultat du traitement de message. 0 si l’opération réussit.

## <a name="remarks"></a>Notes

Pour obtenir un exemple de l’utilisation de ce gestionnaire de messages dans une table des messages, consultez [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)<br/>
[Tables des messages](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)

