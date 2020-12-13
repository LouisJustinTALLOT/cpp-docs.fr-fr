---
description: 'En savoir plus sur : avertissement du compilateur C4430'
title: Avertissement du compilateur C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: af214bb0e9d373ee319008f509ba78f5d7ade38b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344300"
---
# <a name="compiler-warning-c4430"></a>Avertissement du compilateur C4430

spécificateur de type manquant - int est pris en compte par défaut. Remarque : C++ ne prend pas en charge int par défaut

Cette erreur peut être générée en raison du travail de conformité du compilateur effectué pour Visual Studio 2005 : toutes les déclarations doivent spécifier explicitement le type ; int n’est plus utilisé.

C4430 est toujours émis en tant qu’erreur.  Vous pouvez désactiver cet avertissement avec le `#pragma warning` ou **/WD**; consultez [Warning](../../preprocessor/warning.md) ou [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4430.

```cpp
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
