---
title: Fonctions globales de la gestion des événements | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
dev_langs:
- C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb2c7834e7d5475810973a42ef179ea4f5f0079f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358336"
---
# <a name="event-handling-global-functions"></a>Fonctions globales de la gestion des événements
Cette fonction fournit un gestionnaire d’événements.  
  
> [!IMPORTANT]
>  La fonction répertoriée dans le tableau suivant ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
|||  
|-|-|  
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Attend un objet soit signalé, en attendant la distribution des messages de fenêtre en fonction des besoins.|  

## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop  
 Attend que l'objet soit signalé tout en distribuant les messages de fenêtre en fonction des besoins.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```  
  
### <a name="parameters"></a>Paramètres  
 `hEvent`  
 [in] Le handle de l’objet à attendre.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** si l’objet a été signalé.  
  
### <a name="remarks"></a>Notes  
 Cela est utile si vous souhaitez attendre un événement d’un objet à se produire et être averti de ce produit, mais autoriser les messages de fenêtre doit être distribué lors de l’attente.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../atl/reference/atl-functions.md)
