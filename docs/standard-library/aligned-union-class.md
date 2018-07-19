---
title: aligned_union, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::aligned_union
dev_langs:
- C++
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdd2a8417f66c0e095f571c914d5a4624179fdb6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962111"
---
# <a name="alignedunion-class"></a>aligned_union, classe

Fournit un type POD suffisamment grand et convenablement aligné pour stocker un type union et la taille nécessaire.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>Paramètres

*Len* la valeur d’alignement pour le type le plus grand dans l’union.

*Types* types distincts dans l’union sous-jacente.

## <a name="remarks"></a>Notes

Utilisez la classe de modèle pour obtenir l’alignement et la taille nécessaires pour stocker une union dans un stockage non initialisé. Le typedef de membre `type` nomme un type POD adaptés au stockage d’un type énuméré dans *Types*; la taille minimale est *Len*. Le membre statique `alignment_value` de type `std::size_t` contient l’alignement le plus strict nécessaire de tous les types répertoriés dans *Types*.

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

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[alignment_of, classe](../standard-library/alignment-of-class.md)<br/>
