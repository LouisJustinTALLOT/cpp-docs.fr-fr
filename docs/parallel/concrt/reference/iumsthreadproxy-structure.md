---
title: IUMSThreadProxy, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
dev_langs:
- C++
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbba2955adc14ef73a0ba9932756ace57c4136e6
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688607"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy, structure
Abstraction d'un thread d'exécution. Si vous voulez que votre planificateur reçoive des threads UMS (User-Mode Scheduling), affectez à l'élément de stratégie du planificateur `SchedulerKind` la valeur `UmsThreadDefault`, puis implémentez l'interface `IUMSScheduler`. Les threads UMS sont uniquement pris en charge sur les systèmes d'exploitation 64 bits avec Windows 7 et ses versions ultérieures.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IUMSThreadProxy : public IThreadProxy;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Appelé pour entrer dans une zone critique. À l’intérieur d’une région critique, le planificateur ne sera pas équilibrée des opérations de blocage asynchrones se produire lors de la région. Cela signifie que le planificateur ne sera pas être réintroduite de défauts de page, arrêts de thread, les appels de procédure asynchrone du noyau (appel de procédure asynchrone) et ainsi de suite, pour un thread UMS.|  
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Appelé pour accéder à une région hyper critique. À l’intérieur d’une région hyper critique, le planificateur n’observera toutes les opérations de blocage qui se produisent au cours de la région. Cela signifie que le planificateur ne sera pas être réintroduite pour le blocage des appels de fonction, les tentatives de d’acquisition de verrou qui se bloquent, défauts de page, thread suspensions, appels de procédure asynchrone de noyau (appel de procédure asynchrone) et ainsi de suite, pour un UMS de thread.|  
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|Appelé pour quitter une région critique.|  
|[IUMSThreadProxy::ExitHyperCriticalRegion](#exithypercriticalregion)|Appelé pour quitter une région hyper critique.|  
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Retourne le type de région critique se trouve dans le proxy de thread. Étant donné que hyper critiques sont un sur-ensemble de régions critiques, si le code a entré une région critique, puis une région hyper critique, `InsideHyperCriticalRegion` sera retourné.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [IThreadProxy](ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="entercriticalregion"></a>  IUMSThreadProxy::EnterCriticalRegion, méthode  
 Appelé pour entrer dans une zone critique. À l’intérieur d’une région critique, le planificateur ne sera pas équilibrée des opérations de blocage asynchrones se produire lors de la région. Cela signifie que le planificateur ne sera pas être réintroduite de défauts de page, arrêts de thread, les appels de procédure asynchrone du noyau (appel de procédure asynchrone) et ainsi de suite, pour un thread UMS.  
  
```
virtual int EnterCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nouvelle profondeur de la région critique. Les régions critiques sont réentrantes.  
  
##  <a name="enterhypercriticalregion"></a>  IUMSThreadProxy::EnterHyperCriticalRegion, méthode  
 Appelé pour accéder à une région hyper critique. À l’intérieur d’une région hyper critique, le planificateur n’observera toutes les opérations de blocage qui se produisent au cours de la région. Cela signifie que le planificateur ne sera pas être réintroduite pour le blocage des appels de fonction, les tentatives de d’acquisition de verrou qui se bloquent, défauts de page, thread suspensions, appels de procédure asynchrone de noyau (appel de procédure asynchrone) et ainsi de suite, pour un UMS de thread.  
  
```
virtual int EnterHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nouvelle profondeur de la région hyper critique. Régions Hyper critiques sont réentrantes.  
  
### <a name="remarks"></a>Notes  
 Le planificateur doit être extrêmement prudent lorsque vous les méthodes qu’il appelle et quels verrous il acquiert dans ces régions. Si le code dans une région de ce type se bloque sur un verrou est détenu par quelque chose sur que le planificateur est chargé pour la planification, le blocage peut-être survenir.  
  
##  <a name="exitcriticalregion"></a>  IUMSThreadProxy::ExitCriticalRegion, méthode  
 Appelé pour quitter une région critique.  
  
```
virtual int ExitCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nouvelle profondeur de la région critique. Les régions critiques sont réentrantes.  
  
##  <a name="exithypercriticalregion"></a>  IUMSThreadProxy::ExitHyperCriticalRegion, méthode  
 Appelé pour quitter une région hyper critique.  
  
```
virtual int ExitHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nouvelle profondeur de la région hyper critique. Régions Hyper critiques sont réentrantes.  
  
##  <a name="getcriticalregiontype"></a>  IUMSThreadProxy::GetCriticalRegionType, méthode  
 Retourne le type de région critique se trouve dans le proxy de thread. Étant donné que hyper critiques sont un sur-ensemble de régions critiques, si le code a entré une région critique, puis une région hyper critique, `InsideHyperCriticalRegion` sera retourné.  
  
```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le type de région critique se trouve dans le proxy de thread.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [IUMSScheduler, structure](iumsscheduler-structure.md)
