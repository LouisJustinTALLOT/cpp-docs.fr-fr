---
description: 'En savoir plus sur : classe task_handle'
title: task_handle, classe
ms.date: 03/27/2019
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: 21fa2a1782fad200061deb1e85bf052613354a34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188220"
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
Type de l’objet de fonction qui sera appelé pour exécuter le travail représenté par l' `task_handle` objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[task_handle](#task_handle)|Construit un nouvel objet `task_handle`. Le travail de la tâche est effectué en appelant la fonction spécifiée comme paramètre pour le constructeur.|
|[Destructeur ~ task_handle](#dtor)|Détruit l' `task_handle` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[, opérateur ()](#task_handle__operator_call)|Opérateur d’appel de fonction que le runtime appelle pour exécuter le travail du handle de tâche.|

## <a name="remarks"></a>Notes

`task_handle` les objets peuvent être utilisés conjointement avec un `structured_task_group` objet ou un objet plus général `task_group` , pour décomposer le travail en tâches parallèles. Pour plus d’informations, consultez [parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Notez que le créateur d’un `task_handle` objet est chargé de maintenir la durée de vie de l' `task_handle` objet créé jusqu’à ce qu’il ne soit plus requis par le runtime d’accès concurrentiel. En règle générale, cela signifie que l' `task_handle` objet ne doit pas être détruit tant que la `wait` `run_and_wait` méthode ou de `task_group` ou `structured_task_group` à laquelle il est mis en file d’attente n’a pas été appelée.

`task_handle` les objets sont généralement utilisés conjointement avec les expressions lambda C++. Étant donné que vous ne connaissez pas le type réel de l’expression lambda, la fonction [make_task](concurrency-namespace-functions.md#make_task) est généralement utilisée pour créer un `task_handle` objet.

Le runtime crée une copie de la fonction de travail que vous transmettez à un `task_handle` objet. Par conséquent, les modifications d’État qui se produisent dans un objet de fonction que vous transmettez à un `task_handle` objet n’apparaîtront pas dans votre copie de cet objet de fonction.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`task_handle`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrence

## <a name="operator"></a><a name="task_handle__operator_call"></a> , opérateur ()

Opérateur d’appel de fonction que le runtime appelle pour exécuter le travail du handle de tâche.

```cpp
void operator()() const;
```

## <a name="task_handle"></a><a name="task_handle"></a> task_handle

Construit un nouvel objet `task_handle`. Le travail de la tâche est effectué en appelant la fonction spécifiée comme paramètre pour le constructeur.

```cpp
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>Paramètres

*_Func*<br/>
Fonction qui sera appelée pour exécuter le travail représenté par l' `task_handle` objet. Il peut s’agir d’un functor lambda, d’un pointeur vers une fonction ou de tout objet qui prend en charge une version de l’opérateur d’appel de fonction avec la signature `void operator()()` .

### <a name="remarks"></a>Notes

Le runtime crée une copie de la fonction de travail que vous transmettez au constructeur. Par conséquent, les modifications d’État qui se produisent dans un objet de fonction que vous transmettez à un `task_handle` objet n’apparaîtront pas dans votre copie de cet objet de fonction.

## <a name="task_handle"></a><a name="dtor"></a> ~ task_handle

Détruit l' `task_handle` objet.

```cpp
~task_handle();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe task_group](task-group-class.md)<br/>
[Classe structured_task_group](structured-task-group-class.md)
