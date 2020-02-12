---
title: task_handle, classe
ms.date: 03/27/2019
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: a61e72f14448d5033d5be9069ffeec7d3bb08061
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142553"
---
# <a name="task_handle-class"></a>task_handle, classe

La classe `task_handle` représente un élément de travail parallèle individuel. Elle encapsule les instructions et les données requises pour exécuter un élément de travail.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Type de l’objet de fonction qui sera appelé pour exécuter le travail représenté par l’objet `task_handle`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[task_handle](#task_handle)|Construit un nouvel objet `task_handle`. Le travail de la tâche est effectué en appelant la fonction spécifiée comme paramètre pour le constructeur.|
|[Destructeur ~ task_handle](#dtor)|Détruit l’objet `task_handle`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator()](#task_handle__operator_call)|Opérateur d’appel de fonction que le runtime appelle pour exécuter le travail du handle de tâche.|

## <a name="remarks"></a>Notes

les objets `task_handle` peuvent être utilisés conjointement avec un `structured_task_group` ou un objet `task_group` plus général, pour décomposer le travail en tâches parallèles. Pour plus d’informations, consultez [parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Notez que le créateur d’un objet `task_handle` est responsable de la maintenance de la durée de vie de l’objet `task_handle` créé jusqu’à ce qu’il ne soit plus requis par le runtime d’accès concurrentiel. En général, cela signifie que l’objet `task_handle` ne doit pas être détruit tant que la méthode `wait` ou `run_and_wait` de la `task_group` ou `structured_task_group` à laquelle il est mis en file d’attente n’a pas été appelée.

les objets `task_handle` sont généralement utilisés conjointement avec C++ les expressions lambda. Étant donné que vous ne connaissez pas le type réel de l’expression lambda, la fonction [make_task](concurrency-namespace-functions.md#make_task) est généralement utilisée pour créer un objet `task_handle`.

Le runtime crée une copie de la fonction de travail que vous transmettez à un objet `task_handle`. Par conséquent, les modifications d’État qui se produisent dans un objet de fonction que vous transmettez à un objet `task_handle` n’apparaîtront pas dans votre copie de cet objet de fonction.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`task_handle`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrency

## <a name="task_handle__operator_call"></a>, opérateur ()

Opérateur d’appel de fonction que le runtime appelle pour exécuter le travail du handle de tâche.

```cpp
void operator()() const;
```

## <a name="task_handle"></a>task_handle

Construit un nouvel objet `task_handle`. Le travail de la tâche est effectué en appelant la fonction spécifiée comme paramètre pour le constructeur.

```cpp
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>Paramètres

*_Func*<br/>
Fonction qui sera appelée pour exécuter le travail représenté par l’objet `task_handle`. Il peut s’agir d’un functor lambda, d’un pointeur vers une fonction ou de tout objet qui prend en charge une version de l’opérateur d’appel de fonction avec la signature `void operator()()`.

### <a name="remarks"></a>Notes

Le runtime crée une copie de la fonction de travail que vous transmettez au constructeur. Par conséquent, les modifications d’État qui se produisent dans un objet de fonction que vous transmettez à un objet `task_handle` n’apparaîtront pas dans votre copie de cet objet de fonction.

## <a name="dtor"></a>~ task_handle

Détruit l’objet `task_handle`.

```cpp
~task_handle();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Classe task_group](task-group-class.md)<br/>
[structured_task_group, classe](structured-task-group-class.md)
