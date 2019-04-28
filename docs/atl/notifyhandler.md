---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 292a1c6606585dc0694ee678ba8bc9b5fbc42681
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261444"
---
# <a name="notifyhandler"></a>NotifyHandler

Le nom de la fonction identifiée par le troisième paramètre de la macro NOTIFY_HANDLER dans votre table des messages.

## <a name="syntax"></a>Syntaxe

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Paramètres

*idCtrl*<br/>
L’identificateur du contrôle qui envoie le message.

*pnmh*<br/>
Adresse d’un [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) structure qui contient le code de notification et des informations supplémentaires. Pour certains messages de notification, ce paramètre pointe vers une plus grande structure qui a le `NMHDR` structure en tant que son premier membre.

*bHandled*<br/>
Les jeux de mappage de message *bHandled* sur TRUE avant *NotifyHandler* est appelée. Si *NotifyHandler* ne gère pas entièrement le message, il doit définir *bHandled* à **FALSE** pour indiquer le message nécessite un traitement supplémentaire.

## <a name="return-value"></a>Valeur de retour

Le résultat du traitement de message. 0 si l’opération réussit.

## <a name="remarks"></a>Notes

Pour obtenir un exemple de l’utilisation de ce gestionnaire de messages dans une table des messages, consultez [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)<br/>
[Tables des messages](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
