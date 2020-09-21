---
title: Erreur du compilateur C2004
ms.date: 11/04/2016
f1_keywords:
- C2004
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
ms.openlocfilehash: c4f099ba241b56291074202e6c03ad98ee97f756
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743501"
---
# <a name="compiler-error-c2004"></a>Erreur du compilateur C2004

attendu 'defined(id)'

Un identificateur doit apparaître entre les parenthèses qui suivent le mot clé du préprocesseur.

Cette erreur peut également être générée en raison de la mise en conformité du compilateur pour Visual Studio .NET 2003 : parenthèses absentes dans la directive de préprocesseur. Si la parenthèse fermante est absente dans une directive de préprocesseur, le compilateur génère une erreur.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’erreur C2004 :

```cpp
// C2004.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG   // C2004
        printf_s("DEBUG defined\n");
    #endif
}
```

Solution possible :

```cpp
// C2004b.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG)
        printf_s("DEBUG defined\n");
    #endif
}
```
