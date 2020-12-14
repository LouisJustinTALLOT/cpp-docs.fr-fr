---
description: 'En savoir plus sur : classe task_completion_event'
title: task_completion_event, classe
ms.date: 11/04/2016
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
helpviewer_keywords:
- task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
ms.openlocfilehash: 791b68d6a67ea2f8a9697b69266e8744455f845c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188363"
---
# <a name="task_completion_event-class"></a>task_completion_event, classe

La classe `task_completion_event` vous permet de retarder l'exécution d'une tâche jusqu'à ce qu'une condition soit satisfaite, ou de démarrer une tâche en réponse à un événement externe.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```

### <a name="parameters"></a>Paramètres

*_ResultType*<br/>
Type de résultat de cette classe `task_completion_event`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[task_completion_event](#ctor)|Construit un objet `task_completion_event`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[set](#set)|Surchargé. Définit l'événement de fin de tâche.|
|[set_exception](#set_exception)|Surchargé. Propage une exception à toutes les tâches associées à cet événement.|

## <a name="remarks"></a>Notes

Utilisez une tâche créée à partir d’un événement de fin de tâche quand votre scénario vous oblige à créer une tâche qui va se terminer. La continuation de son exécution est ainsi planifiée, à un moment donné dans le futur. Le `task_completion_event` doit avoir le même type que la tâche que vous créez et l'appel de la méthode set sur l'événement de fin de tâche avec une valeur de ce type entraîne la fin de tâche associée et fournit cette valeur comme résultat de la continuation de la tâche.

Si l'événement de fin de tâche n'est jamais signalé, toutes les tâches créées à partir de celle-ci seront annulées durant sa destruction.

`task_completion_event` se comporte comme un pointeur intelligent et doit être passé par valeur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`task_completion_event`

## <a name="requirements"></a>Spécifications

**En-tête :** ppltasks. h

**Espace de noms :** concurrence

## <a name="set"></a><a name="set"></a> définie

Définit l'événement de fin de tâche.

```cpp
bool set(_ResultType _Result) const ;

bool set() const ;
```

### <a name="parameters"></a>Paramètres

*_Result*<br/>
Résultat avec lequel définir cet événement.

### <a name="return-value"></a>Valeur renvoyée

La méthode retourne **`true`** si elle a réussi à définir l’événement. Elle retourne **`false`** si l’événement est déjà défini.

### <a name="remarks"></a>Notes

En présence de plusieurs ou appels simultanés à `set` , seul le premier appel aboutira et son résultat (le cas échéant) sera stocké dans l’événement d’achèvement de la tâche. Les jeux restants sont ignorés et la méthode retourne la valeur false. Lorsque vous définissez un événement d’achèvement de tâche, toutes les tâches créées à partir de cet événement se terminent immédiatement, et ses continuations, le cas échéant, sont planifiées. Les objets d’achèvement de tâche qui ont un `_ResultType` autre que **`void`** transmettent la valeur à leurs continuations.

## <a name="set_exception"></a><a name="set_exception"></a> set_exception

Propage une exception à toutes les tâches associées à cet événement.

```cpp
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```

### <a name="parameters"></a>Paramètres

*_E*<br/>
Type d'exception.

*_Except*<br/>
Exception à définir.

*_ExceptionPtr*<br/>
Pointeur d’exception à définir.

### <a name="return-value"></a>Valeur renvoyée

## <a name="task_completion_event"></a><a name="ctor"></a> task_completion_event

Construit un objet `task_completion_event`.

```cpp
task_completion_event();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
