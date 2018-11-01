---
title: alignment_of, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 2633749a72ceeea197579dca4300b58250f60d73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604394"
---
# <a name="alignmentof-class"></a>alignment_of, classe

Obtient l'alignement du type spécifié. Ce struct est implémenté en termes d’[alignof](../cpp/alignof-and-alignas-cpp.md). Utilisez `alignof` directement quand vous devez simplement interroger une valeur d'alignement. Utilisez alignment_of quand vous avez besoin d’une constante intégrale, par exemple lors de la répartition d’étiquettes.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Paramètres

*Ty*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

La requête de type conserve la valeur de l’alignement du type *Ty*.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage, classe](../standard-library/aligned-storage-class.md)<br/>
