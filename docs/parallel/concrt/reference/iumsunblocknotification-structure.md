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
ms.openlocfilehash: bdf083e2ad418269e49e53dc164f2a60f693d5d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180210"
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
|[IUMSUnblockNotification::GetContext](#getcontext)|Retourne le `IExecutionContext` interface pour le contexte d’exécution associé au proxy de thread qui a été débloqué. Une fois que cette méthode est retournée et le contexte d’exécution sous-jacent a été replanifié via un appel à la `IThreadProxy::SwitchTo` (méthode), cette interface n’est plus valide.|
|[IUMSUnblockNotification::GetNextUnblockNotification](#getnextunblocknotification)|Renvoie la prochaine `IUMSUnblockNotification` interface dans la chaîne retournée par la méthode `IUMSCompletionList::GetUnblockNotifications`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IUMSUnblockNotification`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrtrm.h

**Espace de noms :** concurrency

##  <a name="getcontext"></a>  IUMSUnblockNotification::GetContext Method

Retourne le `IExecutionContext` interface pour le contexte d’exécution associé au proxy de thread qui a été débloqué. Une fois que cette méthode est retournée et le contexte d’exécution sous-jacent a été replanifié via un appel à la `IThreadProxy::SwitchTo` (méthode), cette interface n’est plus valide.

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

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler, structure](iumsscheduler-structure.md)<br/>
[IUMSCompletionList, structure](iumscompletionlist-structure.md)
