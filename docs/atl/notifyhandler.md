---
title: NotifyHandler | Microsoft Docs
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
ms.openlocfilehash: e39b0b1ac94a759c4a8b30fce8c634ed49be4ff9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209477"
---
# <a name="notifyhandler"></a>NotifyHandler
Le nom de la fonction identifiée par le troisième paramètre de la macro NOTIFY_HANDLER dans votre table des messages.  
  
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
 *idCtrl*  
 L’identificateur du contrôle qui envoie le message.  
  
 *pnmh*  
 Adresse d’un [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) structure qui contient le code de notification et des informations supplémentaires. Pour certains messages de notification, ce paramètre pointe vers une plus grande structure qui a le `NMHDR` structure en tant que son premier membre.  
  
 *bHandled*  
 Les jeux de mappage de message *bHandled* sur TRUE avant *NotifyHandler* est appelée. Si *NotifyHandler* ne gère pas entièrement le message, il doit définir *bHandled* à **FALSE** pour indiquer le message nécessite un traitement supplémentaire.  
  
## <a name="return-value"></a>Valeur de retour  
 Le résultat du traitement de message. 0 si l’opération réussit.  
  
## <a name="remarks"></a>Notes  
 Pour obtenir un exemple de l’utilisation de ce gestionnaire de messages dans une table des messages, consultez [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une fenêtre](../atl/implementing-a-window.md)   
 [Tables des messages](../atl/message-maps-atl.md)   
 [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)

