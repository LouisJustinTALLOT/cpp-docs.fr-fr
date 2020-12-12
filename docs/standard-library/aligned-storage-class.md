---
description: 'En savoir plus sur : classe aligned_storage'
title: aligned_storage, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_storage
helpviewer_keywords:
- aligned_storage class
- aligned_storage
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
ms.openlocfilehash: c64be243ff724994cc27a57ce51d7ff0f81b6f9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163676"
---
# <a name="aligned_storage-class"></a>aligned_storage, classe

Crée un type correctement aligné.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Len, std::size_t Align>
struct aligned_storage;

template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>
using aligned_storage_t = typename aligned_storage<Len, Align>::type;
```

### <a name="parameters"></a>Paramètres

*Len*\
Taille de l'objet.

*Droite*\
Alignement de l'objet.

## <a name="remarks"></a>Notes

Le typedef de membre `type` de modèle est un synonyme d’un type Pod avec alignement *align* et Size *Len*. *Align* doit être égal à `alignment_of<T>::value` pour un certain type `T` , ou à l’alignement par défaut.

## <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

typedef std::aligned_storage<sizeof (int),
    std::alignment_of<double>::value>::type New_type;
int main()
    {
    std::cout << "alignment_of<int> == "
        << std::alignment_of<int>::value << std::endl;
    std::cout << "aligned to double == "
        << std::alignment_of<New_type>::value << std::endl;

    return (0);
    }
```

```Output
alignment_of<int> == 4
aligned to double == 8
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](type-traits.md)\
[Classe alignment_of](alignment-of-class.md)
