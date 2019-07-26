---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 58ebd91fb4fa32cf31d2c49429d0445b92fe0c82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449909"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Inclut l’en-tête \<Assert. > h de la bibliothèque standard C et ajoute les noms associés à l' `std` espace de noms. L’inclusion de cet en-tête garantit que les noms déclarés à l’aide de la liaison externe dans l' `std` en-tête de la bibliothèque standard C sont déclarés dans l’espace de noms.

> [!NOTE]
> \<Assert. h > ne définit `static_assert` pas la macro.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cassert>
```

## <a name="macros"></a>Macros

```cpp
#define assert(E)
```

### <a name="remarks"></a>Notes

`assert(E)`est uniquement constant, si NDEBUG est défini à `assert` l’emplacement de la dernière définition ou de la redéfinition de l’objet, ou si *E* convertie en bool a la **valeur true**.

## <a name="see-also"></a>Voir aussi

[Macro assert, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque C++ Standard](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
