---
title: CommandHandler | Microsoft Docs
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
ms.openlocfilehash: 784551b090f7c0c73b96b846fcc8d74017cc1e30
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850639"
---
# <a name="commandhandler"></a>CommandHandler
`CommandHandler` la fonction est identifiée par le troisième paramètre de la macro COMMAND_HANDLER dans votre table des messages.  
  
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
 *wNotifyCode*  
 Le code de notification.  
  
 *wID*  
 L’identificateur de l’élément de menu, un contrôle ou un accélérateur.  
  
 *hWndCtl*  
 Handle vers un contrôle de fenêtre.  
  
 *bHandled*  
 Les jeux de mappage de message *bHandled* sur TRUE avant `CommandHandler` est appelée. Si `CommandHandler` ne gère pas entièrement le message, il doit définir *bHandled* sur FALSE pour indiquer que le message nécessite un traitement supplémentaire.  
  
## <a name="return-value"></a>Valeur de retour  
 Le résultat du traitement de message. 0 si l’opération réussit.  
  
## <a name="remarks"></a>Notes  
 Pour obtenir un exemple de l’utilisation de ce gestionnaire de messages dans une table des messages, consultez [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une fenêtre](../atl/implementing-a-window.md)   
 [Tables des messages](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)

