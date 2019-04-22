---
title: Erreur du compilateur C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 025498f3fe244916cd0a06e36feee6fdb532acc6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026689"
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