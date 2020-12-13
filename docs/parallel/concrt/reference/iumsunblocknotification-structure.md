---
description: 'En savoir plus sur : structure IUMSUnblockNotification,'
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
ms.openlocfilehash: bec40ee1e7326ad37e205c3035f965cb3f0ec8d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334317"
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
|[IUMSUnblockNotification, :: GetContext](#getcontext)|Retourne l' `IExecutionContext` interface pour le contexte d’exécution associé au proxy de thread qui a débloqué. Une fois que cette méthode est retournée et que le contexte d’exécution sous-jacent a été replanifié via un appel à la `IThreadProxy::SwitchTo` méthode, cette interface n’est plus valide.|
|[IUMSUnblockNotification, :: GetNextUnblockNotification](#getnextunblocknotification)|Retourne l' `IUMSUnblockNotification` interface suivante dans la chaîne retournée par la méthode `IUMSCompletionList::GetUnblockNotifications` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IUMSUnblockNotification`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrence

## <a name="iumsunblocknotificationgetcontext-method"></a><a name="getcontext"></a> IUMSUnblockNotification, :: GetContext, méthode

Retourne l' `IExecutionContext` interface pour le contexte d’exécution associé au proxy de thread qui a débloqué. Une fois que cette méthode est retournée et que le contexte d’exécution sous-jacent a été replanifié via un appel à la `IThreadProxy::SwitchTo` méthode, cette interface n’est plus valide.

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

`IExecutionContext`Interface pour le contexte d’exécution d’un proxy de thread qui a débloqué.

## <a name="iumsunblocknotificationgetnextunblocknotification-method"></a><a name="getnextunblocknotification"></a> IUMSUnblockNotification, :: GetNextUnblockNotification, méthode

Retourne l' `IUMSUnblockNotification` interface suivante dans la chaîne retournée par la méthode `IUMSCompletionList::GetUnblockNotifications` .

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Interface suivante `IUMSUnblockNotification` de la chaîne retournée par la méthode `IUMSCompletionList::GetUnblockNotifications` .

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[IUMSScheduler, structure](iumsscheduler-structure.md)<br/>
[IUMSCompletionList, structure](iumscompletionlist-structure.md)
