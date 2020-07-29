---
title: alignment_of, classe
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 5a90f481c33431d92f0f28405e6226863d2b3913
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205013"
---
# <a name="alignment_of-class"></a>alignment_of, classe

Obtient l'alignement du type spécifié. Ce struct est implémenté en termes de [`alignof`](../cpp/alignment-cpp-declarations.md) . Utilisez **`alignof`** directement quand vous devez simplement interroger une valeur d’alignement. Utilisez `alignment_of` lorsque vous avez besoin d’une constante intégrale, par exemple lors de la distribution de balises.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

La requête de type contient la valeur de l’alignement du type *Ty*.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[`<type_traits>`](type-traits.md)\
[`aligned_storage`Type](aligned-storage-class.md)
