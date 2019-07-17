---
title: '&lt;n’importe quel&gt; fonctions'
ms.date: 04/04/2019
f1_keywords:
- any/std::any_cast
- any/std::make_any
- any/std::swap
ms.openlocfilehash: bb5f8b4411477cfcd33613ee0395227dced784f6
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268741"
---
# <a name="ltanygt-functions"></a>&lt;n’importe quel&gt; fonctions

## <a name="any_cast"></a> any_cast

Rend un objet dans un n’importe quel.

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

## <a name="make_any"></a> make_any

Prend les valeurs et crée un objet de n’importe quel.

```cpp
template <class T, class... Args>
    any make_any(Args&& ...args);
template <class T, class U, class... Args>
    any make_any(initializer_list<U> il, Args&& ...args);
```

## <a name="swap"></a> échange

Échange de tous les éléments de deux objets.

```cpp
void swap(any& left, any& right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `any`.

*Oui*\
Objet de type `any`.
