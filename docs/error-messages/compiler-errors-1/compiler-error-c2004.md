---
title: Erreur du compilateur C2004 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2004
dev_langs:
- C++
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b560ef96c4fadcb7c5ce57ece13647032ca9e902
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118750"
---
# <a name="compiler-error-c2004"></a>Erreur du compilateur C2004

attendu 'defined(id)'

Un identificateur doit apparaître entre les parenthèses qui suivent le mot clé du préprocesseur.

Cette erreur peut également être générée en raison de la mise en conformité du compilateur pour Visual Studio .NET 2003 : parenthèses absentes dans la directive de préprocesseur. Si la parenthèse fermante est absente dans une directive de préprocesseur, le compilateur génère une erreur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2004 :

```
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

## <a name="example"></a>Exemple

Solution possible :

```
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