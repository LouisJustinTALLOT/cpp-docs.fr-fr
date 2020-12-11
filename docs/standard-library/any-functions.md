---
description: 'En savoir plus sur : &lt; toutes les &gt; fonctions'
title: '&lt;toutes les &gt; fonctions'
ms.date: 04/04/2019
f1_keywords:
- any/std::any_cast
- any/std::make_any
- any/std::swap
ms.openlocfilehash: 03f699ac5c48962bb32a604a885bc0b3c60c8b22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163390"
---
# <a name="ltanygt-functions"></a>&lt;toutes les &gt; fonctions

## <a name="any_cast"></a><a name="any_cast"></a> any_cast

Crée un objet en un.

```cpp
template<class T>
    T any_cast(const any& operand);
template<class T>
    T any_cast(any& operand);
template<class T>
    T any_cast(any&& operand);
template<class T>
    const T* any_cast(const any* operand) noexcept;
template<class T>
    T* any_cast(any* operand) noexcept;
```

## <a name="make_any"></a><a name="make_any"></a> make_any

Prend des valeurs et crée un objet any.

```cpp
template <class T, class... Args>
    any make_any(Args&& ...args);
template <class T, class U, class... Args>
    any make_any(initializer_list<U> il, Args&& ...args);
```

## <a name="swap"></a><a name="swap"></a> échange

Échange les éléments de deux objets.

```cpp
void swap(any& left, any& right) noexcept;
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `any`.

*Oui*\
Objet de type `any`.
