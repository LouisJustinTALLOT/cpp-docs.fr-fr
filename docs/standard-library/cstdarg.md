---
title: '&lt;cstdarg&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdarg>
helpviewer_keywords:
- cstdarg header
ms.assetid: 639b4ef7-8408-4640-9343-41631f0ab663
ms.openlocfilehash: 0b45d5f591c5394ffa861e75169dce70f53b1baf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448025"
---
# <a name="ltcstdarggt"></a>&lt;cstdarg&gt;

Inclut l’en-tête \<stdarg. > h de la bibliothèque standard C et ajoute les noms associés à l' `std` espace de noms. L’inclusion de cet en-tête garantit que les noms déclarés à l’aide de la liaison externe dans l' `std` en-tête de la bibliothèque standard C sont déclarés dans l’espace de noms.

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

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque C++ Standard](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
