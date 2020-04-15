---
title: IUMSUnblockNotification, structure
ms.date: 11/04/2016
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
ms.openlocfilehash: 0b88ddd4184e982a5e07c536efc301eaa16f4a41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368070"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification, structure

Représente une notification du gestionnaire des ressources qui indique qu'un proxy de thread qui s'est bloqué et qui a déclenché un retour vers le contexte de planification désigné du planificateur s'est débloqué et est prêt à être planifié. Cette interface n'est pas valide une fois que le contexte d'exécution associé du proxy de thread, retourné à partir de la méthode `GetContext`, est replanifié.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IUMSUnblockNotification::GetContext](#getcontext)|Retourne `IExecutionContext` l’interface pour le contexte d’exécution associé au proxy de thread qui s’est débloqué. Une fois que cette méthode revient et que le contexte `IThreadProxy::SwitchTo` d’exécution sous-jacent a été reporté via un appel à la méthode, cette interface n’est plus valide.|
|[IUMSUnblockNotification::GetNextUnblockNotification](#getnextunblocknotification)|Retourne l’interface suivante `IUMSUnblockNotification` dans la `IUMSCompletionList::GetUnblockNotifications`chaîne retournée de la méthode .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IUMSUnblockNotification`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="iumsunblocknotificationgetcontext-method"></a><a name="getcontext"></a>IUMSUnblockNotification::GetContext Méthode

Retourne `IExecutionContext` l’interface pour le contexte d’exécution associé au proxy de thread qui s’est débloqué. Une fois que cette méthode revient et que le contexte `IThreadProxy::SwitchTo` d’exécution sous-jacent a été reporté via un appel à la méthode, cette interface n’est plus valide.

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Valeur de retour

Une `IExecutionContext` interface pour le contexte d’exécution à un proxy de thread qui a débloqué.

## <a name="iumsunblocknotificationgetnextunblocknotification-method"></a><a name="getnextunblocknotification"></a>IUMSUnblockNotification::GetNextUnblockNotification Méthode

Retourne l’interface suivante `IUMSUnblockNotification` dans la `IUMSCompletionList::GetUnblockNotifications`chaîne retournée de la méthode .

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Valeur de retour

L’interface suivante `IUMSUnblockNotification` de la `IUMSCompletionList::GetUnblockNotifications`chaîne est revenue de la méthode .

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler, structure](iumsscheduler-structure.md)<br/>
[IUMSCompletionList, structure](iumscompletionlist-structure.md)
