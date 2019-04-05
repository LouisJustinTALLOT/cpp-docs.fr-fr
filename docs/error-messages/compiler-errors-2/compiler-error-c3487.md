---
title: Erreur du compilateur C3487
ms.date: 11/04/2016
f1_keywords:
- C3487
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
ms.openlocfilehash: 01f8a1bd74ed2b7a3150afae5b46128c6f5b0ca2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028410"
---
# <a name="compiler-error-c3487"></a>Erreur du compilateur C3487

’type de retour’ : toutes les expressions de retour doivent déduire le même type : il s’agissait auparavant de ’type de retour’

Une expression lambda doit spécifier son type de retour, sauf si elle contient une seule instruction return. Si une expression lambda contient plusieurs instructions return, elles doivent toutes avoir le même type.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Spécifiez un type de retour de fin pour l’expression lambda. Vérifiez que tous les retours à partir de l'expression lambda sont du même type ou peuvent être convertis implicitement en type de retour.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3487 car les types de retour de l’expression lambda ne correspondent pas :

```
// C3487.cpp
// Compile by using: cl /c /W4 C3487.cpp

int* test(int* pi) {
   // To fix the error, uncomment the trailing return type below
   auto odd_pointer = [=]() /* -> int* */ {
      if (*pi % 2)
         return pi;
      return nullptr; // C3487 - nullptr is not an int* type
   };
   return odd_pointer();
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)