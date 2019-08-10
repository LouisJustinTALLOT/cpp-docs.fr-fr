---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: d875a039b01b7458a1df46a2539cf5c68aa67e41
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915936"
---
# <a name="notifyhandler"></a>NotifyHandler

Nom de la fonction identifiée par le troisième paramètre de la macro NOTIFY_HANDLER dans votre table des messages.

## <a name="syntax"></a>Syntaxe

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Paramètres

*idCtrl*<br/>
Identificateur du contrôle qui envoie le message.

*pnmh*<br/>
Adresse d’une structure [NMHDR](/windows/desktop/api/richedit/ns-richedit-nmhdr) qui contient le code de notification et des informations supplémentaires. Pour certains messages de notification, ce paramètre pointe vers une structure plus grande qui `NMHDR` a la structure comme premier membre.

*bHandled*<br/>
La table des messages affecte à *bHandled* la valeur true avant l’appel de *notifyhandler* . Si *notifyhandler* ne gère pas complètement le message, il doit affecter à *BHandled* la valeur **false** pour indiquer que le message doit être traité ultérieurement.

## <a name="return-value"></a>Valeur de retour

Résultat du traitement du message. 0 en cas de réussite.

## <a name="remarks"></a>Notes

Pour obtenir un exemple d’utilisation de ce gestionnaire de messages dans une table des messages, consultez [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)<br/>
[Tables des messages](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
