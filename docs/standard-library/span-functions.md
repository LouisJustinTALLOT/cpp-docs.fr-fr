---
title: '&lt;span, &gt; fonctions'
ms.date: 05/28/2020
f1_keywords:
- span/std::span::as_bytes
- span/std::as_writable_bytes
helpviewer_keywords:
- std::span [C++], as_writable_bytes
- std::as_bytes [C++]
ms.openlocfilehash: f51c99d2f2a051a07cefcb985fdb46340fefb3ee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217439"
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

### <a name="return-value"></a>Valeur de retour

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

### <a name="return-value"></a>Valeur de retour

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
