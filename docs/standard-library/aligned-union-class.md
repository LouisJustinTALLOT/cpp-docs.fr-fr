---
title: aligned_union, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: ae03802549f7791e51dccf1ea98a7b18929a4a4b
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690108"
---
# <a name="aligned_union-class"></a>aligned_union, classe

Fournit un type POD suffisamment grand et convenablement aligné pour stocker un type union et la taille nécessaire.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>Paramètres

*Len* \
Valeur d'alignement pour le plus grand type dans l'union.

*Types*\
Types distincts dans l'union sous-jacente.

## <a name="remarks"></a>Notes

Utilisez le modèle de classe pour obtenir l’alignement et la taille nécessaires pour stocker une Union dans le stockage non initialisé. Le typedef de membre `type` nomme un type POD approprié pour le stockage de tout type listé dans les *types*; la taille minimale est *Len*. Le membre statique `alignment_value` de type `std::size_t` contient l’alignement le plus strict requis de tous les types listés dans *types*.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser `aligned_union` pour allouer une mémoire tampon de pile alignée afin de placer une union.

```cpp
// std__type_traits__aligned_union.cpp
#include <iostream>
#include <type_traits>

union U_type
{
    int i;
    float f;
    double d;
    U_type(float e) : f(e) {}
};

typedef std::aligned_union<16, int, float, double>::type aligned_U_type;

int main()
{
    // allocate memory for a U_type aligned on a 16-byte boundary
    aligned_U_type au;
    // do placement new in the aligned memory on the stack
    U_type* u = new (&au) U_type(1.0f);
    if (nullptr != u)
    {
        std::cout << "value of u->i is " << u->i << std::endl;
        // must clean up placement objects manually!
        u->~U_type();
    }
}
```

```Output
value of u->i is 1065353216
```

## <a name="requirements"></a>spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[alignment_of, classe](../standard-library/alignment-of-class.md)
