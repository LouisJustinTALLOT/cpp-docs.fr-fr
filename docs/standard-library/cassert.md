---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: b28f4554610d37b881494748f75499f46cd9e8d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230231"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Inclut l’en-tête de la bibliothèque standard C \<assert.h> et ajoute les noms associés à l' `std` espace de noms. L’inclusion de cet en-tête garantit que les noms déclarés à l’aide de la liaison externe dans l’en-tête de la bibliothèque standard C sont déclarés dans l' `std` espace de noms.

> [!NOTE]
> \<assert.h>ne définit pas la **`static_assert`** macro.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cassert>
```

## <a name="macros"></a>Macros

```cpp
#define assert(E)
```

### <a name="remarks"></a>Notes

`assert(E)`est uniquement constant, si NDEBUG est défini à l’emplacement de la `assert` dernière définition ou de la redéfinition de l’objet, ou si *E* convertie en bool a la valeur **`true`** .

## <a name="see-also"></a>Voir aussi

[Macro Assert, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
