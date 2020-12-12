---
description: 'En savoir plus sur : &lt; cstdarg&gt;'
title: '&lt;cstdarg&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdarg>
helpviewer_keywords:
- cstdarg header
ms.assetid: 639b4ef7-8408-4640-9343-41631f0ab663
ms.openlocfilehash: 4f009535cdcfec5d9e461aad4857335ddb86e1ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233251"
---
# <a name="ltcstdarggt"></a>&lt;cstdarg&gt;

Inclut l’en-tête de la bibliothèque standard C \<stdarg.h> et ajoute les noms associés à l' `std` espace de noms. L’inclusion de cet en-tête garantit que les noms déclarés à l’aide de la liaison externe dans l’en-tête de la bibliothèque standard C sont déclarés dans l' `std` espace de noms.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cstdarg>
```

## <a name="namespace-and-macros"></a>Espace de noms et macros

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

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
