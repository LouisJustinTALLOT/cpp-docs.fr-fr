---
title: Avertissement du compilateur (niveau 4) C4668
ms.date: 11/04/2016
f1_keywords:
- C4668
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
ms.openlocfilehash: 11d96941a1efddde87068af8829e24259f2fa312
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408158"
---
# <a name="compiler-warning-level-4-c4668"></a>Avertissement du compilateur (niveau 4) C4668

'symbole' non défini comme préprocesseur ou macro, remplacement par '0' pour 'directives'

Un symbole non défini a été utilisé avec une directive de préprocesseur. Le symbole correspond à false. Pour définir un symbole, vous pouvez utiliser la [#define, directive](../../preprocessor/hash-define-directive-c-cpp.md) ou [/D](../../build/reference/d-preprocessor-definitions.md) option du compilateur.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4668 :

```
// C4668.cpp
// compile with: /W4
#include <stdio.h>

#pragma warning (default : 4668)   // turn warning on

int main()
{
    #if q   // C4668, q is not defined
        printf_s("defined");
    #else
        printf_s("undefined");
    #endif
}
```