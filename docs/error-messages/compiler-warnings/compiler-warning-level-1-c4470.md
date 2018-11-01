---
title: Avertissement du compilateur (niveau 1) C4470
ms.date: 11/04/2016
f1_keywords:
- C4470
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
ms.openlocfilehash: 7fd4644ab39e350c0c0badb527875b427a2c6987
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531060"
---
# <a name="compiler-warning-level-1-c4470"></a>Avertissement du compilateur (niveau 1) C4470

pragmas de contrôle à virgule flottante ignorés sous /clr

Les pragmas de contrôle à virgule flottante :

- [fenv_access](../../preprocessor/fenv-access.md)

- [float_control](../../preprocessor/float-control.md)

- [fp_contract](../../preprocessor/fp-contract.md)

n’ont aucun effet sous [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

L’exemple suivant génère l’erreur C4470 :

```
// C4470.cpp
// compile with: /clr /W1 /LD
#pragma float_control(except, on)   // C4470
```