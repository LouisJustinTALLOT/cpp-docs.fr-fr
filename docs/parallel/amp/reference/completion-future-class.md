---
description: 'En savoir plus sur : classe completion_future'
title: completion_future, classe
ms.date: 11/04/2016
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
ms.openlocfilehash: 8cf252bc29dc85014cb6375eab18de98d6d31646
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247850"
---
# <a name="completion_future-class"></a>completion_future, classe

Représente un futur correspondant à une C++ AMP opération asynchrone.

## <a name="syntax"></a>Syntaxe

```cpp
class completion_future;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur completion_future](#ctor)|Initialise une nouvelle instance de la classe `completion_future`.|
|[Destructeur ~ completion_future](#dtor)|Détruit l' `completion_future` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get](#get)|Attend que l’opération asynchrone associée se termine.|
|[Cliquez](#then)|Chaîne un objet de fonction de rappel à l' `completion_future` objet à exécuter lorsque l’exécution de l’opération asynchrone associée se termine.|
|[to_task](#to_task)|Retourne un `task` objet correspondant à l’opération asynchrone associée.|
|[valide](#valid)|Obtient une valeur booléenne qui indique si l’objet est associé à une opération asynchrone.|
|[wait](#wait)|Bloque jusqu’à ce que l’opération asynchrone associée se termine.|
|[wait_for](#wait_for)|Bloque jusqu’à ce que l’opération asynchrone associée se termine ou que l’heure spécifiée par `_Rel_time` soit écoulée.|
|[wait_until](#wait_until)|Bloque jusqu’à ce que l’opération asynchrone associée se termine ou jusqu’à ce que l’heure actuelle dépasse la valeur spécifiée par `_Abs_time` .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur std :: shared_future\<void>](#operator_shared_future)|Convertit implicitement l' `completion_future` objet en `std::shared_future` objet.|
|[opérateur =](#operator_eq)|Copie le contenu de l’objet spécifié dans celui- `completion_future` ci.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`completion_future`

## <a name="requirements"></a>Spécifications

**En-tête :** amprt. h

**Espace de noms :** concurrence

## <a name="completion_future"></a><a name="ctor"></a> completion_future

Initialise une nouvelle instance de la classe `completion_future`.

### <a name="syntax"></a>Syntaxe

```cpp
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
`completion_future`Objet à copier ou déplacer.

### <a name="overloads-list"></a>Liste des surcharges

|Nom|Description|
|----------|-----------------|
|`completion_future();`|Initialise une nouvelle instance de la `completion_future` classe.|
|`completion_future(const completion_future& _Other);`|Initialise une nouvelle instance de la `completion_future` classe en copiant un constructeur.|
|`completion_future(completion_future&& _Other);`|Initialise une nouvelle instance de la `completion_future` classe en déplaçant un constructeur.|

## <a name="get"></a><a name="get"></a> Télécharger

Attend que l’opération asynchrone associée se termine. Lève l’exception stockée si une exception a été rencontrée pendant l’opération asynchrone.

### <a name="syntax"></a>Syntaxe

```cpp
void get() const;
```

## <a name="operator-stdshared_futurevoid"></a><a name="operator_shared_future"></a> opérateur std :: shared_future\<void>

Convertit implicitement l' `completion_future` objet en `std::shared_future` objet.

### <a name="syntax"></a>Syntaxe

```cpp
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>Valeur de retour

Objet `std::shared_future`.

## <a name="operator"></a><a name="operator_eq"></a> opérateur =

Copie le contenu de l’objet spécifié dans celui- `completion_future` ci.

### <a name="syntax"></a>Syntaxe

```cpp
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur renvoyée

Référence à cet `completion_future` objet.

## <a name="overloads-list"></a>Liste des surcharges

|Nom|Description|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|Copie le contenu de l’objet spécifié dans celui- `completion_future` ci, à l’aide d’une copie complète.|
|`completion_future& operator=(completion_future&& _Other);`|Copie le contenu de l’objet spécifié dans celui- `completion_future` ci, à l’aide d’une assignation de déplacement.|

## <a name="then"></a><a name="then"></a> Cliquez

Chaîne un objet de fonction de rappel à l' `completion_future` objet à exécuter lorsque l’exécution de l’opération asynchrone associée se termine.

### <a name="syntax"></a>Syntaxe

```cpp
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>Paramètres

*_Functor*<br/>
Functor de rappel.

*_Func*<br/>
Objet de fonction de rappel.

## <a name="to_task"></a><a name="to_task"></a> to_task

Retourne un `task` objet correspondant à l’opération asynchrone associée.

### <a name="syntax"></a>Syntaxe

```cpp
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>Valeur de retour

`task`Objet correspondant à l’opération asynchrone associée.

## <a name="valid"></a><a name="valid"></a> valide

Obtient une valeur booléenne qui indique si l’objet est associé à une opération asynchrone.

### <a name="syntax"></a>Syntaxe

```cpp
bool valid() const;
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si l’objet est associé à une opération asynchrone ; Sinon, **`false`** .

## <a name="wait"></a><a name="wait"></a> qu'

Bloque jusqu’à ce que l’opération asynchrone associée se termine.

### <a name="syntax"></a>Syntaxe

```cpp
void wait() const;
```

## <a name="wait_for"></a><a name="wait_for"></a> wait_for

Bloque jusqu’à ce que l’opération asynchrone associée se termine ou que l’heure spécifiée par `_Rel_time` soit écoulée.

### <a name="syntax"></a>Syntaxe

```cpp
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>Paramètres

*_Rep*<br/>
Type arithmétique qui représente le nombre de graduations.

*_Period*<br/>
Std :: ratio qui représente le nombre de secondes qui s’écoulent avant chaque battement.

*_Rel_time*<br/>
Durée maximale d'attente d'achèvement de l'opération.

### <a name="return-value"></a>Valeur renvoyée

Retourne les informations suivantes :

- `std::future_status::deferred` Si l’opération asynchrone associée n’est pas en cours d’exécution.

- `std::future_status::ready` Si l’opération asynchrone associée est terminée.

- `std::future_status::timeout` Si la période spécifiée s’est écoulée.

## <a name="wait_until"></a><a name="wait_until"></a> wait_until

Bloque jusqu’à ce que l’opération asynchrone associée se termine ou jusqu’à ce que l’heure actuelle dépasse la valeur spécifiée par `_Abs_time` .

### <a name="syntax"></a>Syntaxe

```cpp
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>Paramètres

*_Clock*<br/>
Horloge sur laquelle ce point temporel est mesuré.

*_Duration*<br/>
Intervalle de temps depuis le début de l' `_Clock` époque de la fonction, après quoi la fonction expire.

*_Abs_time*<br/>
Point dans le temps au-delà duquel la fonction expire.

### <a name="return-value"></a>Valeur renvoyée

Retourne les informations suivantes :

1. `std::future_status::deferred` Si l’opération asynchrone associée n’est pas en cours d’exécution.

1. `std::future_status::ready` Si l’opération asynchrone associée est terminée.

1. `std::future_status::timeout` Si la durée spécifiée est écoulée.

## <a name="completion_future"></a><a name="dtor"></a> ~ completion_future

Détruit l' `completion_future` objet.

### <a name="syntax"></a>Syntaxe

```cpp
~completion_future();
```

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
