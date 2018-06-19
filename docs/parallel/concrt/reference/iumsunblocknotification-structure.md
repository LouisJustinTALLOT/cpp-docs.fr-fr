---
title: IUMSUnblockNotification, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
dev_langs:
- C++
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bda4f6e2b0565d39fd604767f3a89bcdd9a6df2c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687005"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification, structure
Représente une notification du gestionnaire des ressources qui indique qu'un proxy de thread qui s'est bloqué et qui a déclenché un retour vers le contexte de planification désigné du planificateur s'est débloqué et est prêt à être planifié. Cette interface n'est pas valide une fois que le contexte d'exécution associé du proxy de thread, retourné à partir de la méthode `GetContext`, est replanifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IUMSUnblockNotification;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IUMSUnblockNotification::GetContext](#getcontext)|Retourne le `IExecutionContext` interface pour le contexte d’exécution associé au proxy de thread qui a été débloqué. Une fois que cette méthode est retournée et le contexte d’exécution sous-jacent replanifié via un appel à la `IThreadProxy::SwitchTo` (méthode), cette interface n’est plus valide.|  
|[IUMSUnblockNotification::GetNextUnblockNotification](#getnextunblocknotification)|Renvoie la prochaine `IUMSUnblockNotification` interface dans la chaîne retournée par la méthode `IUMSCompletionList::GetUnblockNotifications`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IUMSUnblockNotification`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="getcontext"></a>  IUMSUnblockNotification::GetContext, méthode  
 Retourne le `IExecutionContext` interface pour le contexte d’exécution associé au proxy de thread qui a été débloqué. Une fois que cette méthode est retournée et le contexte d’exécution sous-jacent replanifié via un appel à la `IThreadProxy::SwitchTo` (méthode), cette interface n’est plus valide.  
  
```
virtual IExecutionContext* GetContext() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `IExecutionContext` interface pour le contexte d’exécution d’un proxy de thread qui a été débloqué.  
  
##  <a name="getnextunblocknotification"></a>  IUMSUnblockNotification::GetNextUnblockNotification, méthode  
 Renvoie la prochaine `IUMSUnblockNotification` interface dans la chaîne retournée par la méthode `IUMSCompletionList::GetUnblockNotifications`.  
  
```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 La prochaine `IUMSUnblockNotification` interface dans la chaîne retournée par la méthode `IUMSCompletionList::GetUnblockNotifications`.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [IUMSScheduler, Structure](iumsscheduler-structure.md)   
 [IUMSCompletionList, structure](iumscompletionlist-structure.md)
