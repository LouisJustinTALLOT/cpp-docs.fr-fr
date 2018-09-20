---
title: IUMSThreadProxy, Structure | Microsoft Docs
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
ms.openlocfilehash: 573bee042788f03278abc78fbc541c933d693907
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417382"
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
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Appelé pour accéder à une zone critique. À l’intérieur d’une zone critique, le planificateur ne sera pas équilibrée des opérations de blocage asynchrones qui se produisent au cours de la région. Cela signifie que le planificateur ne sera pas être entrés de nouveau pour les défauts de page, arrêts de thread, appels de procédure asynchrone du noyau (APC) et ainsi de suite, pour un thread UMS.|
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Appelé pour accéder à une zone hyper critique. À l’intérieur d’une zone hyper critique, le planificateur respectent pas les opérations de blocage qui se produisent pendant la région. Cela signifie que le planificateur ne sera pas nouvelle saisie pour le blocage des appels de fonction, les tentatives d’acquisition de verrou qui se bloquent, défauts de page, thread suspensions, appels de procédure asynchrone du noyau (APC) et ainsi de suite, pour un UMS thread.|
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|Appelé pour quitter une zone critique.|
|[IUMSThreadProxy::ExitHyperCriticalRegion](#exithypercriticalregion)|Appelé pour quitter une zone hyper critique.|
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Retourne le type de région critique, le proxy de thread est dans. Étant donné que hyper critiques sont un sur-ensemble de régions critiques, si le code a entré une zone critique, puis une région hyper stratégiques, `InsideHyperCriticalRegion` sera retourné.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrtrm.h

**Espace de noms :** concurrency

##  <a name="entercriticalregion"></a>  IUMSThreadProxy::EnterCriticalRegion, méthode

Appelé pour accéder à une zone critique. À l’intérieur d’une zone critique, le planificateur ne sera pas équilibrée des opérations de blocage asynchrones qui se produisent au cours de la région. Cela signifie que le planificateur ne sera pas être entrés de nouveau pour les défauts de page, arrêts de thread, appels de procédure asynchrone du noyau (APC) et ainsi de suite, pour un thread UMS.

```
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

Nouvelle profondeur de la zone critique. Les zones critiques sont réentrants.

##  <a name="enterhypercriticalregion"></a>  IUMSThreadProxy::EnterHyperCriticalRegion, méthode

Appelé pour accéder à une zone hyper critique. À l’intérieur d’une zone hyper critique, le planificateur respectent pas les opérations de blocage qui se produisent pendant la région. Cela signifie que le planificateur ne sera pas nouvelle saisie pour le blocage des appels de fonction, les tentatives d’acquisition de verrou qui se bloquent, défauts de page, thread suspensions, appels de procédure asynchrone du noyau (APC) et ainsi de suite, pour un UMS thread.

```
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

Nouvelle profondeur de la zone hyper critique. Régions Hyper critiques sont réentrantes.

### <a name="remarks"></a>Notes

Le planificateur doit être extrêmement prudent de qu’elle appelle des méthodes et quels verrous il acquiert dans ces régions. Si le code dans ces régions se bloque sur un verrou est détenu par quelque chose sur que le planificateur est chargé de planifier, d’interblocage peut en découler.

##  <a name="exitcriticalregion"></a>  IUMSThreadProxy::ExitCriticalRegion, méthode

Appelé pour quitter une zone critique.

```
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

Nouvelle profondeur de la zone critique. Les zones critiques sont réentrants.

##  <a name="exithypercriticalregion"></a>  IUMSThreadProxy::ExitHyperCriticalRegion, méthode

Appelé pour quitter une zone hyper critique.

```
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

Nouvelle profondeur de la zone hyper critique. Régions Hyper critiques sont réentrantes.

##  <a name="getcriticalregiontype"></a>  IUMSThreadProxy::GetCriticalRegionType, méthode

Retourne le type de région critique, le proxy de thread est dans. Étant donné que hyper critiques sont un sur-ensemble de régions critiques, si le code a entré une zone critique, puis une région hyper stratégiques, `InsideHyperCriticalRegion` sera retourné.

```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Le type de région critique le proxy de thread se trouve dans.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler, structure](iumsscheduler-structure.md)
