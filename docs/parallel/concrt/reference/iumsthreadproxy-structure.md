---
title: IUMSThreadProxy, structure
ms.date: 11/04/2016
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
ms.openlocfilehash: f4fb43a4223cad8cc63049d2a0f8345e48b90f17
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139962"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy, structure

Abstraction d'un thread d'exécution. Si vous voulez que votre planificateur reçoive des threads UMS (User-Mode Scheduling), affectez à l'élément de stratégie du planificateur `SchedulerKind` la valeur `UmsThreadDefault`, puis implémentez l'interface `IUMSScheduler`. Les threads UMS sont uniquement pris en charge sur les systèmes d'exploitation 64 bits avec Windows 7 et ses versions ultérieures.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[IUMSThreadProxy :: EnterCriticalRegion](#entercriticalregion)|Appelé pour entrer dans une zone critique. Lorsqu’il se trouve dans une région critique, le planificateur ne respecte pas les opérations de blocage asynchrone qui se produisent pendant la région. Cela signifie que le planificateur ne sera pas réentré pour les erreurs de page, les suspensions de thread, les appels de procédure asynchrone du noyau (APC), etc., pour un thread UMS.|
|[IUMSThreadProxy :: EnterHyperCriticalRegion](#enterhypercriticalregion)|Appelé pour entrer dans une zone hyper-critique. Dans une région hyper-critique, le planificateur ne respecte pas les opérations bloquantes qui se produisent pendant la région. Cela signifie que le planificateur ne sera pas de nouveau entré pour bloquer les appels de fonction, les tentatives d’acquisition de verrous, le bloc, les défauts de page, les suspensions de thread, les appels de procédure asynchrone du noyau (APC), etc., pour un thread UMS.|
|[IUMSThreadProxy :: ExitCriticalRegion](#exitcriticalregion)|Appelé pour quitter une région critique.|
|[IUMSThreadProxy :: ExitHyperCriticalRegion](#exithypercriticalregion)|Appelé pour quitter une région hyper-critique.|
|[IUMSThreadProxy :: GetCriticalRegionType](#getcriticalregiontype)|Retourne le type de région critique dans lequel se trouve le proxy de thread. Étant donné que les régions hyper-critiques sont un sur-ensemble de régions critiques, si le code a entré une région critique et une région hyper-critique, `InsideHyperCriticalRegion` est renvoyé.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrency

## <a name="entercriticalregion"></a>IUMSThreadProxy :: EnterCriticalRegion, méthode

Appelé pour entrer dans une zone critique. Lorsqu’il se trouve dans une région critique, le planificateur ne respecte pas les opérations de blocage asynchrone qui se produisent pendant la région. Cela signifie que le planificateur ne sera pas réentré pour les erreurs de page, les suspensions de thread, les appels de procédure asynchrone du noyau (APC), etc., pour un thread UMS.

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

Nouvelle profondeur de la région critique. Les régions critiques sont réentrantes.

## <a name="enterhypercriticalregion"></a>IUMSThreadProxy :: EnterHyperCriticalRegion, méthode

Appelé pour entrer dans une zone hyper-critique. Dans une région hyper-critique, le planificateur ne respecte pas les opérations bloquantes qui se produisent pendant la région. Cela signifie que le planificateur ne sera pas de nouveau entré pour bloquer les appels de fonction, les tentatives d’acquisition de verrous, le bloc, les défauts de page, les suspensions de thread, les appels de procédure asynchrone du noyau (APC), etc., pour un thread UMS.

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

Nouvelle profondeur de la région hyper-critique. Les régions hyper-critiques sont réentrantes.

### <a name="remarks"></a>Notes

Le planificateur doit être très prudent en ce qui concerne les méthodes qu’il appelle et les verrous qu’il acquière dans ces régions. Si du code dans une telle région se bloque sur un verrou détenu par un rôle que le planificateur est responsable de la planification, un interblocage peut se dérouler.

## <a name="exitcriticalregion"></a>IUMSThreadProxy :: ExitCriticalRegion, méthode

Appelé pour quitter une région critique.

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

Nouvelle profondeur de la région critique. Les régions critiques sont réentrantes.

## <a name="exithypercriticalregion"></a>IUMSThreadProxy :: ExitHyperCriticalRegion, méthode

Appelé pour quitter une région hyper-critique.

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

Nouvelle profondeur de la région hyper-critique. Les régions hyper-critiques sont réentrantes.

## <a name="getcriticalregiontype"></a>IUMSThreadProxy :: GetCriticalRegionType, méthode

Retourne le type de région critique dans lequel se trouve le proxy de thread. Étant donné que les régions hyper-critiques sont un sur-ensemble de régions critiques, si le code a entré une région critique et une région hyper-critique, `InsideHyperCriticalRegion` est renvoyé.

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Type de région critique dans lequel se trouve le proxy de thread.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler, structure](iumsscheduler-structure.md)
