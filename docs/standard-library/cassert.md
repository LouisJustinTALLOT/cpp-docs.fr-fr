---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 14dda03e835ec411013b2d827bd1ccaa77f8982e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245018"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Inclut l’en-tête de bibliothèque C Standard \<assert.h > et ajoute les noms associés à la `std` espace de noms. Inclusion de cet en-tête garantit également que les noms déclarés à l’aide d’une liaison externe dans l’en-tête de bibliothèque C Standard sont déclarés dans le `std` espace de noms.

> [!NOTE]
> \<Assert.h > ne définit pas le `static_assert` macro.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cassert>
```

## <a name="macros"></a>Macros

```cpp
#define assert(E)
```

### <a name="remarks"></a>Notes

`assert(E)` est uniquement constant, s’il est défini de NDEBUG où `assert` est dernière définies ou redéfinies, ou *E* converti en bool a la valeur **true**.

## <a name="see-also"></a>Voir aussi

[assert (macro), _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
