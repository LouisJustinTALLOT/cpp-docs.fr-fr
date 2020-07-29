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
ms.openlocfilehash: e7321831b9356fdb9ae5ce147319726def69efc7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215567"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt;, opérateurs

||||
|-|-|-|
|[opérateur ! =](#op_neq)|[and&gt;](#op_gt)|[and&gt;=](#op_gt_eq)|
|[and&lt;](#op_lt)|[and&lt;&lt;](#op_lt_lt)|[and&lt;=](#op_lt_eq)|
|[opérateur = =](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>and&gt;=

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

## <a name="operatorgt"></a><a name="op_gt"></a>and&gt;

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

## <a name="operatorlt"></a><a name="op_lt_eq"></a>and&lt;=

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

## <a name="operatorlt"></a><a name="op_lt"></a>and&lt;

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

**`true`** Si la *partie gauche* précède *le classement* total ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

L’opérateur définit un classement total sur tous les objets `thread::id`. Ces objets peuvent être utilisés comme clés dans les conteneurs associatifs.

Cette fonction ne lève aucune exception.

## <a name="operator"></a><a name="op_neq"></a>opérateur ! =

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

## <a name="operator"></a><a name="op_eq_eq"></a>opérateur = =

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

**`true`** Si les deux objets représentent le même thread d’exécution ou si aucun objet ne représente un thread d’exécution ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>and&lt;&lt;

Insère une représentation textuelle d’un objet `thread::id` dans un flux.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Paramètres

*OSTR*\
Objet [basic_ostream](../standard-library/basic-ostream-class.md).

*Identifi*\
Objet `thread::id`.

### <a name="return-value"></a>Valeur de retour

*OSTR*.

### <a name="remarks"></a>Notes

Cette fonction insère l' *ID* dans *OSTR*.

Si deux objets `thread::id` sont considérés égaux, les représentations textuelles insérées de ces objets sont identiques.

## <a name="see-also"></a>Voir aussi

[\<thread>](../standard-library/thread.md)
