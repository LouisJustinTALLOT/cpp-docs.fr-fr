---
title: shared_future, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
dev_langs:
- C++
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: 2ac125b068de5111a2b98800956c12a0c979737f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859662"
---
# <a name="sharedfuture-class"></a>shared_future, classe

Décrit un *objet retour asynchrone*. Contrairement à un objet [future](../standard-library/future-class.md), un *fournisseur asynchrone* peut être associé à un nombre quelconque d’objets `shared_future`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Notes

N’appelez pas d’autres méthodes que `valid`, `operator=` et le destructeur sur un objet `shared_future` qui est *vide*.

Les objets `shared_future` ne sont pas synchronisés. L’appel de méthodes sur le même objet par plusieurs threads provoque une concurrence critique des données qui a des résultats imprévisibles.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[shared_future](#shared_future)|Construit un objet `shared_future`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get](#get)|Récupère le résultat qui est stocké dans l’*état asynchrone associé*.|
|[valid](#valid)|Spécifie si l’objet n’est pas vide.|
|[attente](#wait)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt.|
|[wait_for](#wait_for)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt ou que le délai spécifié soit écoulé.|
|[wait_until](#wait_until)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt ou jusqu’à un point spécifié dans le temps.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|Assigne un nouvel état asynchrone associé.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<future >

**Espace de noms :** std

## <a name="get"></a>  shared_future::Get

Récupère le résultat qui est stocké dans l’*état asynchrone associé*.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Notes

Si le résultat est une exception, la méthode la lève de nouveau. Sinon, le résultat est retourné.

Avant de récupérer le résultat, cette méthode bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt.

Pour la spécialisation partielle `shared_future<Ty&>`, la valeur stockée est une référence à l’objet qui a été passé au *fournisseur asynchrone* comme valeur de retour.

Comme il n’y a pas de valeur stockée pour la spécialisation `shared_future<void>`, la méthode retourne `void`.

## <a name="op_eq"></a>  shared_future::operator=

Transfère un *état asynchrone associé* à partir d’un objet spécifié.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Paramètres

`Right` A `shared_future` objet.

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Notes

Pour le premier opérateur, `Right` n’a plus d’état asynchrone associé après l’opération.

Pour la deuxième méthode, `Right` conserve son état asynchrone associé.

## <a name="shared_future"></a>  shared_future::shared_future, constructeur

Construit un objet `shared_future`.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Paramètres

`Right` A [futures](../standard-library/future-class.md) ou `shared_future` objet.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet `shared_future` sans *état asynchrone associé*.

Les deuxième et troisième constructeurs construisent un objet `shared_future`, et transfèrent l’état asynchrone associé à partir de `Right`. `Right` n’a plus d’état asynchrone associé.

Le quatrième constructeur construit un objet `shared_future` qui a le même état asynchrone associé que `Right`.

## <a name="valid"></a>  shared_future::Valid

Spécifie si l’objet a un *état asynchrone associé*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Valeur de retour

`true` si l'objet possède un état asynchrone associé ; sinon, `false`.

## <a name="wait"></a>  shared_future::wait

Bloque le thread actuel jusqu’à ce que *l’état asynchrone associé* soit *prêt*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Notes

Un état asynchrone associé est prêt uniquement si son fournisseur asynchrone a stocké une valeur de retour ou une exception.

## <a name="wait_for"></a>  shared_future::wait_for

Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit *prêt* ou que le temps spécifié soit écoulé.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Paramètres

`Rel_time` A [chrono::duration](../standard-library/duration-class.md) objet qui spécifie un intervalle de temps maximal que le thread se bloque.

### <a name="return-value"></a>Valeur de retour

[future_status](../standard-library/future-enums.md#future_status) qui indique la raison du retour.

### <a name="remarks"></a>Notes

Un état asynchrone associé est *prêt* uniquement si son fournisseur asynchrone a stocké une valeur de retour ou une exception.

## <a name="wait_until"></a>  shared_future::wait_until

Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit *prêt* ou jusqu’à un point spécifié dans le temps.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Paramètres

`Abs_time` A [chrono::time_point](../standard-library/time-point-class.md) objet qui spécifie une durée après laquelle le thread peut débloquer.

### <a name="return-value"></a>Valeur de retour

[future_status](../standard-library/future-enums.md#future_status) qui indique la raison du retour.

### <a name="remarks"></a>Notes

Un état asynchrone associé est prêt uniquement si son fournisseur asynchrone a stocké une valeur de retour ou une exception.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
