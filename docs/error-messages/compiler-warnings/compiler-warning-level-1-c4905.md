---
title: Compilateur avertissement (niveau 1) C4905 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4905
dev_langs:
- C++
helpviewer_keywords:
- C4905
ms.assetid: 40240bf4-b14e-4c22-aeb2-52f2851532f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dffc6c0f2e4ed5e70e5c8f6689b257a66dec72b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089318"
---
# <a name="compiler-warning-level-1-c4905"></a>Avertissement du compilateur (niveau 1) C4905

cast de littéral de chaîne étendu en 'LPSTR'

Le compilateur a détecté un cast non sécurisé. La conversion a réussi, mais vous devez utiliser une routine de conversion.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

L’exemple suivant génère C4905.

```
// C4905.cpp
// compile with: /W1
#pragma warning(default : 4905)
#include <windows.h>
#include <stdlib.h>
#include <stdio.h>

int main()
{
    LPSTR y = (LPSTR)L"1234";   // C4905

    // try the following lines instead
    // wchar_t y[128];
    // size_t  sizeOfConverted;
    // errcode err = 0;
    //
    // err = mbstowcs_s(&sizeOfConverted, &y[0], 128, "12345", 4);
    // if (err != 0)
    // {
    //     printf_s("mbstowcs_s failed!");
    //     exit (-1);
    // }
    // wprintf(L"%s\n", y);

    return 0;
}
```