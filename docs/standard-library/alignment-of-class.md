---
title: alignment_of, classe
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: d241848edf57fe4876c35e22f1762abf5d6888fa
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302313"
---
# <a name="alignment_of-class"></a>alignment_of, classe

Obtient l'alignement du type spécifié. Ce struct est implémenté en termes d’[alignof](../cpp/alignment-cpp-declarations.md). Utilisez **alignof** directement quand vous devez simplement interroger une valeur d’alignement. Utilisez alignment_of quand vous avez besoin d’une constante intégrale, par exemple lors de la répartition d’étiquettes.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parameters

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

La requête de type contient la valeur de l’alignement du type *Ty*.

## <a name="requirements"></a>Configuration requise pour

**En-tête :** \<type_traits >

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[aligned_storage, classe](../standard-library/aligned-storage-class.md)
