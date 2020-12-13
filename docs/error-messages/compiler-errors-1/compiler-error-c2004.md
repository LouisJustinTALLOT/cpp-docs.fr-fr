---
description: 'En savoir plus sur : erreur du compilateur C2004'
title: Erreur du compilateur C2004
ms.date: 11/04/2016
f1_keywords:
- C2004
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
ms.openlocfilehash: f418d2c2c372b228cc50b82237d8ebc56321e2c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340383"
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
