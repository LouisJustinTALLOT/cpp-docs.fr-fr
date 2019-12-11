---
title: Avertissement du compilateur (niveau 4) C4668
ms.date: 11/04/2016
f1_keywords:
- C4668
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
ms.openlocfilehash: 84834ce0f980502e16a8398d35da85d1a005c9cb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990547"
---
# <a name="compiler-warning-level-4-c4668"></a>Avertissement du compilateur (niveau 4) C4668

'symbole' non défini comme préprocesseur ou macro, remplacement par '0' pour 'directives'

Un symbole qui n’a pas été défini a été utilisé avec une directive de préprocesseur. Le symbole prend la valeur false. Pour définir un symbole, vous pouvez utiliser la [directive #define](../../preprocessor/hash-define-directive-c-cpp.md) ou l’option du compilateur [/d](../../build/reference/d-preprocessor-definitions.md) .

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4668 :

```cpp
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
