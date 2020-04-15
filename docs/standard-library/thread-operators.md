---
title: '&lt;thread&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 6312d14dc681736ee396d5c7af6c50ba8d72cd3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375834"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt;, opérateurs

||||
|-|-|-|
|[opérateur!](#op_neq)|[Opérateur&gt;](#op_gt)|[Opérateur&gt;=](#op_gt_eq)|
|[Opérateur&lt;](#op_lt)|[Opérateur&lt;&lt;](#op_lt_lt)|[Opérateur&lt;=](#op_lt_eq)|
|[opérateur](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Opérateur&gt;=

Détermine si un objet `thread::id` est supérieur ou égal à un autre.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet gauche `thread::id`.

*Oui*\
Objet droit `thread::id`.

### <a name="return-value"></a>Valeur de retour

`!(Left < Right)`

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operatorgt"></a><a name="op_gt"></a>Opérateur&gt;

Détermine si un objet `thread::id` est supérieur à un autre.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet gauche `thread::id`.

*Oui*\
Objet droit `thread::id`.

### <a name="return-value"></a>Valeur de retour

`Right < Left`

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Opérateur&lt;=

Détermine si un objet `thread::id` est inférieur ou égal à un autre.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet gauche `thread::id`.

*Oui*\
Objet droit `thread::id`.

### <a name="return-value"></a>Valeur de retour

`!(Right < Left)`

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operatorlt"></a><a name="op_lt"></a>Opérateur&lt;

Détermine si un objet `thread::id` est inférieur à un autre.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet gauche `thread::id`.

*Oui*\
Objet droit `thread::id`.

### <a name="return-value"></a>Valeur de retour

**vrai** si *la gauche* précède *la droite* dans la commande totale; autrement, **faux**.

### <a name="remarks"></a>Notes

L’opérateur définit un classement total sur tous les objets `thread::id`. Ces objets peuvent être utilisés comme clés dans les conteneurs associatifs.

Cette fonction ne lève aucune exception.

## <a name="operator"></a><a name="op_neq"></a>opérateur!

Compare deux objets `thread::id` pour déterminer s'ils sont différents.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet gauche `thread::id`.

*Oui*\
Objet droit `thread::id`.

### <a name="return-value"></a>Valeur de retour

`!(Left == Right)`

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operator"></a><a name="op_eq_eq"></a>opérateur

Compare deux objets `thread::id` pour déterminer s’ils sont égaux.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet gauche `thread::id`.

*Oui*\
Objet droit `thread::id`.

### <a name="return-value"></a>Valeur de retour

**vrai** si les deux objets représentent le même fil d’exécution ou si aucun des deux objets ne représente un fil d’exécution; autrement, **faux**.

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>Opérateur&lt;&lt;

Insère une représentation textuelle d’un objet `thread::id` dans un flux.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Paramètres

*Ostr*\
Objet [basic_ostream](../standard-library/basic-ostream-class.md).

*Id*\
Objet `thread::id` .

### <a name="return-value"></a>Valeur de retour

*Ostr*.

### <a name="remarks"></a>Notes

Cette fonction insère *Id* dans *Ostr*.

Si deux objets `thread::id` sont considérés égaux, les représentations textuelles insérées de ces objets sont identiques.

## <a name="see-also"></a>Voir aussi

[\<>de fil](../standard-library/thread.md)
