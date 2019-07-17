---
title: '&lt;cstdarg&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdarg>
helpviewer_keywords:
- cstdarg header
ms.assetid: 639b4ef7-8408-4640-9343-41631f0ab663
ms.openlocfilehash: f8d2d3b886cfa46905e8f17f1e13b51881b80191
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244485"
---
# <a name="ltcstdarggt"></a>&lt;cstdarg&gt;

Inclut l’en-tête de bibliothèque C Standard \<stdarg.h > et ajoute les noms associés à la `std` espace de noms. Inclusion de cet en-tête garantit également que les noms déclarés à l’aide d’une liaison externe dans l’en-tête de bibliothèque C Standard sont déclarés dans le `std` espace de noms.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cstdarg>
```

## <a name="namespace-and-macros"></a>Namespace et Macros

```cpp
namespace std {
    using va_list = see below;
}

#define va_arg(V, P)
#define va_copy(VDST, VSRC)
#define va_end(V)
#define va_start(V, P)
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
