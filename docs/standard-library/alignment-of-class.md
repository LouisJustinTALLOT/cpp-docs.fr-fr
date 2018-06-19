---
title: alignment_of, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::alignment_of
dev_langs:
- C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7d9ba59d7f1539f690d7b04c70139c263490368
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850689"
---
# <a name="alignmentof-class"></a>alignment_of, classe

Obtient l'alignement du type spécifié. Ce struct est implémenté en termes d’[alignof](../cpp/alignof-and-alignas-cpp.md). Utilisez `alignof` directement quand vous devez simplement interroger une valeur d'alignement. Utilisez alignment_of quand vous avez besoin d’une constante intégrale, par exemple lors de la répartition d’étiquettes.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Paramètres

`Ty` Type à interroger.

## <a name="remarks"></a>Notes

La requête de type contient la valeur de l'alignement du type `Ty`.

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage, classe](../standard-library/aligned-storage-class.md)<br/>
