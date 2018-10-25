---
title: MessageHandler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- MessageHandler
dev_langs:
- C++
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0c7d76ff3b1e05d482b365150c9072a9fdd8d5c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076709"
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
[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)
