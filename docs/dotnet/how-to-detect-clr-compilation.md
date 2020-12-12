---
description: 'En savoir plus sur : Comment : détecter la compilation/CLR'
title: 'Comment : détecter-compilation CLR'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, detecting /clr
- /clr compiler option [C++], detecting use of
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
ms.openlocfilehash: 25cd241a08f79bcae629c05fb3c7982a387120ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175714"
---
# <a name="how-to-detect-clr-compilation"></a>Comment : détecter une compilation /clr

Utilisez la `_MANAGED` `_M_CEE` macro ou pour déterminer si un module est compilé avec **/CLR**. Pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

Pour plus d’informations sur les macros, consultez [macros prédéfinies](../preprocessor/predefined-macros.md).

## <a name="example"></a>Exemple

```cpp
// detect_CLR_compilation.cpp
// compile with: /clr
#include <stdio.h>

int main() {
   #if (_MANAGED == 1) || (_M_CEE == 1)
      printf_s("compiling with /clr\n");
   #else
      printf_s("compiling without /clr\n");
   #endif
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
