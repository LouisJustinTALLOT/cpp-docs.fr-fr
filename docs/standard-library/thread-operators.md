---
description: 'En savoir plus sur &lt; : &gt; opérateurs de thread'
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
ms.openlocfilehash: 3992dccf051622bcf854c1843f1bdeb15d227731
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207421"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt;, opérateurs

[opérateur ! =](#op_neq)\
[and&gt;](#op_gt)\
[and&gt;=](#op_gt_eq)\
[and&lt;](#op_lt)\
[and&lt;&lt;](#op_lt_lt)\
[and&lt;=](#op_lt_eq)\
[opérateur = =](#op_eq_eq)

## <a name="operatorgt"></a><a name="op_gt_eq"></a> and&gt;=

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

### <a name="return-value"></a>Valeur renvoyée

`!(Left < Right)`

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operatorgt"></a><a name="op_gt"></a> and&gt;

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

### <a name="return-value"></a>Valeur renvoyée

`Right < Left`

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operatorlt"></a><a name="op_lt_eq"></a> and&lt;=

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

### <a name="return-value"></a>Valeur renvoyée

`!(Right < Left)`

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

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

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la *partie gauche* précède *le classement* total ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

L’opérateur définit un classement total sur tous les objets `thread::id`. Ces objets peuvent être utilisés comme clés dans les conteneurs associatifs.

Cette fonction ne lève aucune exception.

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

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

### <a name="return-value"></a>Valeur renvoyée

`!(Left == Right)`

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

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

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les deux objets représentent le même thread d’exécution ou si aucun objet ne représente un thread d’exécution ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> and&lt;&lt;

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

### <a name="return-value"></a>Valeur renvoyée

*OSTR*.

### <a name="remarks"></a>Notes

Cette fonction insère l' *ID* dans *OSTR*.

Si deux objets `thread::id` sont considérés égaux, les représentations textuelles insérées de ces objets sont identiques.

## <a name="see-also"></a>Voir aussi

[\<thread>](../standard-library/thread.md)
