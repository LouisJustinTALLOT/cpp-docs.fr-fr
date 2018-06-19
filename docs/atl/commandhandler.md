---
title: CommandHandler | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CommandHandler
dev_langs:
- C++
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27f5585ec334a4179b76579c5216c8c30013ca97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355136"
---
# <a name="commandhandler"></a>CommandHandler
`CommandHandler` est la fonction identifiée par le troisième paramètre de la `COMMAND_HANDLER` macro dans votre table des messages.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 
    LRESULT 
    CommandHandler 
 (
    WORD wNotifyCode,  
    WORD wID,  
    HWND hWndCtl,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Paramètres  
 `wNotifyCode`  
 Le code de notification.  
  
 *wID*  
 Identificateur de l’élément de menu, le contrôle ou l’accélérateur.  
  
 *hWndCtl*  
 Handle vers un contrôle de fenêtre.  
  
 `bHandled`  
 Les jeux de mappage de message `bHandled` à **TRUE** avant `CommandHandler` est appelée. Si `CommandHandler` ne gère pas entièrement le message, il doit définir `bHandled` à **FALSE** pour indiquer le message nécessite un traitement supplémentaire.  
  
## <a name="return-value"></a>Valeur de retour  
 Le résultat du traitement du message. 0 en cas de réussite.  
  
## <a name="remarks"></a>Notes  
 Pour obtenir un exemple d’utilisation de ce gestionnaire de messages dans une table des messages, consultez [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une fenêtre](../atl/implementing-a-window.md)   
 [Tables des messages](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)

