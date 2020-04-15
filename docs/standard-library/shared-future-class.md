---
title: shared_future, classe
ms.date: 11/04/2016
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.openlocfilehash: 65ea01a9ced1ca69cd1b1526e7594c4b54387553
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336780"
---
# <a name="shared_future-class"></a>shared_future, classe

Décrit un *objet de retour asynchrone*. Contrairement à un objet [future](../standard-library/future-class.md), un *fournisseur asynchrone* peut être associé à un nombre quelconque d’objets `shared_future`.

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
|[Valide](#valid)|Spécifie si l’objet n’est pas vide.|
|[Attendre](#wait)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt.|
|[wait_for](#wait_for)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt ou que le délai spécifié soit écoulé.|
|[wait_until](#wait_until)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt ou jusqu’à un point spécifié dans le temps.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[shared_future::opérateur](#op_eq)|Assigne un nouvel état asynchrone associé.|

## <a name="requirements"></a>Spécifications

**En-tête:** \<future>

**Espace de noms :** std

## <a name="shared_futureget"></a><a name="get"></a>shared_future::obtenir

Récupère le résultat qui est stocké dans l’*état asynchrone associé*.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Notes

Si le résultat est une exception, la méthode la lève de nouveau. Sinon, le résultat est retourné.

Avant de récupérer le résultat, cette méthode bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt.

Pour la spécialisation `shared_future<Ty&>`partielle, la valeur stockée est effectivement une référence à l’objet qui a été transmis au fournisseur *asynchrone* comme valeur de retour.

Parce qu’aucune valeur stockée `shared_future<void>`n’existe pour la spécialisation, la méthode retourne **nulle**.

## <a name="shared_futureoperator"></a><a name="op_eq"></a>shared_future::opérateur

Transfère un *état asynchrone associé* à partir d’un objet spécifié.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `shared_future` .

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Notes

Pour le premier opérateur, *Right* n’a plus d’état asynchrone associé après l’opération.

Pour la deuxième méthode, *Right* maintient son état asynchrone associé.

## <a name="shared_futureshared_future-constructor"></a><a name="shared_future"></a>shared_future::shared_future Constructeur

Construit un objet `shared_future`.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet [future](../standard-library/future-class.md) ou `shared_future`.

### <a name="remarks"></a>Notes

Le premier constructeur construit `shared_future` un objet qui n’a pas *d’état asynchrone associé.*

Les deuxième et troisième `shared_future` constructeurs construisent un objet et transfèrent l’état asynchrone associé de *droite.* *Droit* n’a plus d’état asynchrone associé.

Le quatrième constructeur construit `shared_future` un objet qui a le même état asynchrone associé à *droite*.

## <a name="shared_futurevalid"></a><a name="valid"></a>shared_future::valide

Précise si l’objet a un *état asynchrone associé*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Valeur de retour

**vrai** si l’objet a un état asynchrone associé; autrement, **faux**.

## <a name="shared_futurewait"></a><a name="wait"></a>shared_future::attendez

Bloque le fil actuel jusqu’à ce que *l’état asynchrone associé* soit *prêt.*

```cpp
void wait() const;
```

### <a name="remarks"></a>Notes

Un état asynchrone associé est prêt uniquement si son fournisseur asynchrone a stocké une valeur de retour ou une exception.

## <a name="shared_futurewait_for"></a><a name="wait_for"></a>shared_future::wait_for

Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit *prêt* ou que le temps spécifié soit écoulé.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Paramètres

*Rel_time*\
Objet [chrono::duration](../standard-library/duration-class.md) qui spécifie un intervalle de temps maximal pour le blocage du thread.

### <a name="return-value"></a>Valeur de retour

[future_status](../standard-library/future-enums.md#future_status) qui indique la raison du retour.

### <a name="remarks"></a>Notes

Un état asynchrone associé n’est *prêt* que si son fournisseur asynchrone a stocké une valeur de retour ou stocké une exception.

## <a name="shared_futurewait_until"></a><a name="wait_until"></a>shared_future::wait_until

Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit *prêt* ou jusqu’à un point spécifié dans le temps.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Paramètres

*Abs_time*\
Objet [chrono::time_point](../standard-library/time-point-class.md) qui spécifie un point dans le temps après lequel le thread peut être débloqué.

### <a name="return-value"></a>Valeur de retour

[future_status](../standard-library/future-enums.md#future_status) qui indique la raison du retour.

### <a name="remarks"></a>Notes

Un état asynchrone associé est prêt uniquement si son fournisseur asynchrone a stocké une valeur de retour ou une exception.

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<>avenir](../standard-library/future.md)
