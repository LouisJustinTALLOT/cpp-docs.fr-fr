---
description: 'En savoir plus sur &lt; : &gt; fonctions span'
title: '&lt;span, &gt; fonctions'
ms.date: 05/28/2020
f1_keywords:
- span/std::span::as_bytes
- span/std::as_writable_bytes
helpviewer_keywords:
- std::span [C++], as_writable_bytes
- std::as_bytes [C++]
ms.openlocfilehash: 09d712d6dfffee2aa24e0e8cecca4031a27923f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169188"
---
# <a name="ltspangt-functions"></a>&lt;span, &gt; fonctions

L' \<span> en-tête comprend les fonctions non-membres suivantes qui opèrent sur des objets **span** .

| **Fonctions non-membres** | **Description** |
|-|-|
|[as_bytes](#as_bytes) | Obtenir une vue en lecture seule de la représentation sous forme d’objet des éléments de l’étendue. |
|[as_writable_bytes](#as_writable_bytes) | Obtient une vue en lecture/écriture de la représentation sous forme d’objet des éléments de l’étendue. |

## <a name="as_bytes"></a>`as_bytes`

Obtenir une vue en lecture seule de la représentation sous forme d’objet des éléments de l’étendue.

```cpp
template <class T, size_t Extent>
auto as_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>Paramètres

*T*\
Type des éléments de l’étendue.

*Étendue*\
Nombre d’éléments dans l’étendue (s’il est connu au moment de la compilation), sinon `dynamic_extent` indique que le nombre d’éléments n’est pas connu jusqu’à l’exécution.

*x*\
Étendue pour laquelle la représentation brute doit être obtenue.

### <a name="return-value"></a>Valeur renvoyée

`span<const byte, S>`Au premier élément stocké dans l’étendue où `S` est`{reinterpret_cast<const std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = std::as_bytes(mySpan);
}
```

## <a name="as_writable_bytes"></a>`as_writable_bytes`

`T` **`const`** Dans le cas contraire, obtient une vue en lecture/écriture de la représentation d’octets bruts des éléments de l’étendue.

```cpp
template <class T, size_t Extent>
auto as_writable_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>Paramètres

*T*\
Type des éléments de l’étendue.

*Étendue*\
Nombre d’éléments dans l’étendue (s’il est connu au moment de la compilation), sinon `dynamic_extent` indique que le nombre d’éléments n’est pas connu jusqu’à l’exécution.

*x*\
Étendue pour laquelle la représentation brute doit être obtenue.

### <a name="return-value"></a>Valeur renvoyée

`span<byte, S>`Au premier élément stocké dans l’étendue où `S` est`{reinterpret_cast<std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = as_writable_bytes(mySpan);
}
```

## <a name="see-also"></a>Voir aussi

[\<span>](span.md)
