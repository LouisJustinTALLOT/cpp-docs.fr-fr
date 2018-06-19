---
title: NotifyHandler | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- NotifyHandler
dev_langs:
- C++
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74fbdd99c162b4362339d8c1b45ddc281d30eeee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356451"
---
# <a name="notifyhandler"></a>NotifyHandler
Le nom de la fonction identifiée par le troisième paramètre de la `NOTIFY_HANDLER` macro dans votre table des messages.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 
    LRESULT 
    NotifyHandler 
 (
    int idCtrl,  
    LPNMHDR pnmh,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Paramètres  
 `idCtrl`  
 L’identificateur du contrôle qui envoie le message.  
  
 *pnmh*  
 Adresse d’une [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) structure qui contient le code de notification et des informations supplémentaires. Pour certains messages de notification, ce paramètre pointe vers une structure plus importante qui a le **NMHDR** structure en tant que son premier membre.  
  
 `bHandled`  
 Les jeux de mappage de message `bHandled` à **TRUE** avant *NotifyHandler* est appelée. Si *NotifyHandler* ne gère pas entièrement le message, il doit définir `bHandled` à **FALSE** pour indiquer le message nécessite un traitement supplémentaire.  
  
## <a name="return-value"></a>Valeur de retour  
 Le résultat du traitement du message. 0 en cas de réussite.  
  
## <a name="remarks"></a>Notes  
 Pour obtenir un exemple d’utilisation de ce gestionnaire de messages dans une table des messages, consultez [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une fenêtre](../atl/implementing-a-window.md)   
 [Tables des messages](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)

