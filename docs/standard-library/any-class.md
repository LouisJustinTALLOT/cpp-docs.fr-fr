---
description: 'En savoir plus sur : toute classe'
title: toute classe
ms.date: 04/04/2019
f1_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
helpviewer_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
ms.openlocfilehash: 1ff32693e216657bdc9057a7dd7899d9bc479b02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163416"
---
# <a name="any-class"></a>toute classe

Stocke une instance de n’importe quel type qui répond aux exigences du constructeur ou n’a aucune valeur, appelée état de la classe tout objet.

L’instance stockée est appelée valeur contenue. Deux États sont les mêmes s’ils n’ont pas de valeur, ou les deux ont une valeur et les valeurs contenues sont les mêmes.

## <a name="syntax"></a>Syntaxe

```cpp
class any
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[aux](#any)|Construit un objet de type `any`.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[emplace](#emplace)|Définit une valeur any.|
|[has_value](#has_value)|Retourne **`true`** si un a une valeur.|
|[reset](#reset)|Réinitialise un.|
|[swap](#swap)|Échange deux objets.|
|[type](#type)|Retourne le type any.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur =](#op_eq)|Remplace any par une copie d’un autre.|

## <a name="any"></a><a name="any"></a> aux

Construit un objet de type `any`. Comprend également un destructeur.

```cpp
constexpr any() noexcept;
any(const any& other);
any(any&& other) noexcept;
template <class T>
    any(T&& value);
template <class T, class... Args>
    explicit any(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    explicit any(in_place_type_t<T>, initializer_list<U>, Args&&...);

~any();
```

## <a name="emplace"></a><a name="emplace"></a> emplace

Définit une valeur any.

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a><a name="has_value"></a> has_value

Retourne **`true`** si un a une valeur.

```cpp
bool has_value() const noexcept;
```

## <a name="operator"></a><a name="op_eq"></a> opérateur =

Remplace any par une copie d’un autre.

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Tout en cours de copie dans le.

## <a name="reset"></a><a name="reset"></a> initialisation

Réinitialise un.

```cpp
void reset() noexcept;
```

## <a name="swap"></a><a name="swap"></a> échange

Échange deux objets.

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a>Type<a name="type"></a>

Retourne le type any.

```cpp
const type_info& type() const noexcept;
```
