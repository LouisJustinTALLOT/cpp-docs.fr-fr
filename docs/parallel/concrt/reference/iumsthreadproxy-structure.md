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
ms.openlocfilehash: 2e748b1da02394e1f70afd8b92947e1291957c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368082"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy, structure

Abstraction d'un thread d'exécution. Si vous voulez que votre planificateur reçoive des threads UMS (User-Mode Scheduling), affectez à l'élément de stratégie du planificateur `SchedulerKind` la valeur `UmsThreadDefault`, puis implémentez l'interface `IUMSScheduler`. Les threads UMS sont uniquement pris en charge sur les systèmes d'exploitation 64 bits avec Windows 7 et ses versions ultérieures.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Appelé afin d’entrer dans une région critique. À l’intérieur d’une région critique, le planificateur n’observera pas les opérations de blocage asynchrones qui se produisent dans la région. Cela signifie que le planificateur ne sera pas réintégré pour les défauts de page, suspensions de thread, grains asynchrones appels de procédure (APC), et ainsi de suite, pour un thread UMS.|
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Appelé afin d’entrer dans une région hyper-critique. Lorsqu’il se trouve à l’intérieur d’une région hyper-critique, le planificateur n’observera aucune opération de blocage qui se produit dans la région. Cela signifie que le planificateur ne sera pas réintégré pour les appels de fonction de blocage, les tentatives d’acquisition de verrouillage qui bloquent, les défauts de page, les suspensions de fil, les appels de procédure asynchrones de noyau (APC), et ainsi de suite, pour un fil UMS.|
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|Appelé pour sortir d’une région critique.|
|[IUMSThreadProxy::ExitHyperCriticalRegion](#exithypercriticalregion)|Appelé pour sortir d’une région hyper-critique.|
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Retourne dans quel type de région critique le proxy fil est à l’intérieur. Parce que les régions hyper-critiques sont un superset de régions critiques, `InsideHyperCriticalRegion` si le code est entré dans une région critique, puis une région hyper-critique, sera retourné.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[IThreadProxy (en)](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a>IUMSThreadProxy::Méthode De la réélection critique

Appelé afin d’entrer dans une région critique. À l’intérieur d’une région critique, le planificateur n’observera pas les opérations de blocage asynchrones qui se produisent dans la région. Cela signifie que le planificateur ne sera pas réintégré pour les défauts de page, suspensions de thread, grains asynchrones appels de procédure (APC), et ainsi de suite, pour un thread UMS.

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

La nouvelle profondeur de la région critique. Les régions critiques sont réentrantes.

## <a name="iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a>IUMSThreadProxy::EnterHyperCriticalRegion Méthode

Appelé afin d’entrer dans une région hyper-critique. Lorsqu’il se trouve à l’intérieur d’une région hyper-critique, le planificateur n’observera aucune opération de blocage qui se produit dans la région. Cela signifie que le planificateur ne sera pas réintégré pour les appels de fonction de blocage, les tentatives d’acquisition de verrouillage qui bloquent, les défauts de page, les suspensions de fil, les appels de procédure asynchrones de noyau (APC), et ainsi de suite, pour un fil UMS.

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

La nouvelle profondeur de la région hyper-critique. Les régions hyper-critiques sont réentrantes.

### <a name="remarks"></a>Notes

Le planificateur doit faire très attention aux méthodes qu’il appelle et aux verrous qu’il acquiert dans ces régions. Si le code dans une telle région bloque sur un verrou qui est tenu par quelque chose que le planificateur est responsable de la planification, l’impasse peut s’ensuivre.

## <a name="iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a>IUMSThreadProxy::ExitCriticalRegion Method

Appelé pour sortir d’une région critique.

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

La nouvelle profondeur de la région critique. Les régions critiques sont réentrantes.

## <a name="iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a>IUMSThreadProxy::ExitHyperCriticalRegion Méthode

Appelé pour sortir d’une région hyper-critique.

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valeur de retour

La nouvelle profondeur de la région hyper-critique. Les régions hyper-critiques sont réentrantes.

## <a name="iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a>IUMSThreadProxy::GetCriticalRegionType Méthode

Retourne dans quel type de région critique le proxy fil est à l’intérieur. Parce que les régions hyper-critiques sont un superset de régions critiques, `InsideHyperCriticalRegion` si le code est entré dans une région critique, puis une région hyper-critique, sera retourné.

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Le type de région critique le proxy de thread est à l’intérieur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler, structure](iumsscheduler-structure.md)
