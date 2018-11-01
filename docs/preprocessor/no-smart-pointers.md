---
title: no_smart_pointers
ms.date: 11/04/2016
f1_keywords:
- no_search_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 305c08497a600f602767496cba48d108335fdeb8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636980"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**Spécifique à C++**

Supprime la création des pointeurs intelligents pour toutes les interfaces dans la bibliothèque de types.

## <a name="syntax"></a>Syntaxe

```
no_smart_pointers
```

## <a name="remarks"></a>Notes

Par défaut, lorsque vous utilisez `#import`, vous obtenez une déclaration de pointeur intelligent pour toutes les interfaces dans la bibliothèque de types. Ces pointeurs intelligents sont de type [_com_ptr_t, classe](../cpp/com-ptr-t-class.md).

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)