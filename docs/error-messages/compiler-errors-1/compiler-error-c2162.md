---
title: Erreur du compilateur C2162
ms.date: 11/04/2016
f1_keywords:
- C2162
helpviewer_keywords:
- C2162
ms.assetid: 34923628-d35e-48ab-9072-b95e3b5f6b45
ms.openlocfilehash: 02c0101324b28ebe548c38c6dc617faaa62315b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602398"
---
# <a name="compiler-error-c2162"></a>Erreur du compilateur C2162

paramètre formel de macro attendu

Le jeton suivant un opérateur d’enchaînement (#) n’est pas un nom de paramètre formel.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2162 :

```
// C2162.cpp
// compile with: /c
#include <stdio.h>

#define print(a) printf_s(b)   // OK
#define print(a) printf_s(#b)    // C2162
```