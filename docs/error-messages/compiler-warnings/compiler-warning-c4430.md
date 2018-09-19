---
title: Avertissement du compilateur C4430 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4430
dev_langs:
- C++
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79c0045b568a24ad6702e748e82a8ebd88c41044
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093920"
---
# <a name="compiler-warning-c4430"></a>Avertissement du compilateur C4430

spécificateur de type manquant - int est pris en compte par défaut. Remarque : C++ ne prend pas en charge int par défaut

Cette erreur peut être due à la mise en conformité du compilateur pour Visual C++ 2005 : toutes les déclarations doivent spécifier explicitement le type ; int est supposé ne sont plus.

C4430 est toujours émis en tant qu’erreur.  Vous pouvez désactiver cet avertissement avec le `#pragma warning` ou **WD**; consultez [avertissement](../../preprocessor/warning.md) ou [wln, / W0, W1, W2, / w3, / W4, W1, W2, / w3, / W4, Wall, WD, / we, Wo, / WV, /WX (niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md)pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère C4430.

```
// C4430.cpp
// compile with: /c
struct CMyClass {
   CUndeclared m_myClass;  // C4430
   int m_myClass;  // OK
};

typedef struct {
   POINT();   // C4430
   // try the following line instead
   // int POINT();
   unsigned x;
   unsigned y;
} POINT;
```