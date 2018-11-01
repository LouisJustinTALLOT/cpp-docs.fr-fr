---
title: Erreur du compilateur C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: c0075bf0e3749966a5e5b9fcd775b5d73171bf17
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599418"
---
# <a name="compiler-error-c3496"></a>Erreur du compilateur C3496

'this' est toujours capturé par valeur : '&' ignoré

Vous ne pouvez pas capturer le pointeur `this` par référence.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Capturez le pointeur `this` par valeur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3496, car une référence au pointeur `this` se trouve dans la liste de capture d’une expression lambda :

```
// C3496.cpp
// compile with: /c

class C
{
   void f()
   {
      [&this] {}(); // C3496
   }
};
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)