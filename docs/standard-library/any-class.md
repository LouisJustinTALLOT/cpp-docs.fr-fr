---
title: n’importe quelle classe
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
ms.openlocfilehash: 050276da665ab6ed3eb53d9e65bfea06b88bcbea
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268751"
---
# <a name="any-class"></a>n’importe quelle classe

Stocke une instance de n’importe quel type qui satisfait les exigences de constructeur, ou il n’a aucune valeur, qui est appelée à l’état de la classe n’importe quel objet.

L’instance stockée est appelée à la valeur de relation contenant-contenue. Deux États sont les mêmes si elles n’ont aucune valeur, ou disposer d’une valeur, et pour les valeurs de relation contenant-contenus sont les mêmes.

## <a name="syntax"></a>Syntaxe

```cpp
class any
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[any](#any)|Construit un objet de type `any`.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[emplace](#emplace)|Définit une valeur de n’importe quel.|
|[has_value](#has_value)|Retourne **true** si une a une valeur.|
|[reset](#reset)|Réinitialise des.|
|[swap](#swap)|Échange deux tous les objets.|
|[type](#type)|Retourne n’importe quel type.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator=](#op_eq)|Remplace tout le tout avec une copie d’un autre.|

## <a name="any"></a> N’importe quel

Construit un objet de type `any`. Inclut également un destructeur.

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

## <a name="emplace"></a> emplace

Définit une valeur de n’importe quel.

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a> has_value

Retourne **true** si une a une valeur.

```cpp
bool has_value() const noexcept;
```

## <a name="op_eq"></a> opérateur =

Remplace tout le tout avec une copie d’un autre.

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Toutes copiées dans aucune.

## <a name="reset"></a> Réinitialiser

Réinitialise des.

```cpp
void reset() noexcept;
```

## <a name="swap"></a> échange

Échange deux tous les objets.

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a> Type

Retourne n’importe quel type.

```cpp
const type_info& type() const noexcept;
```
