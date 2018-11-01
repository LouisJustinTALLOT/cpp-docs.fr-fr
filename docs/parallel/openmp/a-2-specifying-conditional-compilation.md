---
title: A.2   Spécification de compilation conditionnelle
ms.date: 11/04/2016
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
ms.openlocfilehash: 92ae22ffac1b1a1c3fc45a9a7a883203ff6d251e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491219"
---
# <a name="a2---specifying-conditional-compilation"></a>A.2   Spécification de compilation conditionnelle

Les exemples suivants illustrent l’utilisation de la compilation conditionnelle à l’aide de la macro OpenMP `_OPENMP` ([Section 2.2](../../parallel/openmp/2-2-conditional-compilation.md) page 8). Avec la compilation de OpenMP, le `_OPENMP` macro est définie.

```
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

L’opérateur de préprocesseur défini permet plusieurs macros à tester dans une directive unique.

```
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```