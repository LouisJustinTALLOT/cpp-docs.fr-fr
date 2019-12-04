---
title: Erreur du compilateur C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: b9542f1904c6797a77c88c88a37aff9348364268
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738178"
---
# <a name="compiler-error-c3496"></a>Erreur du compilateur C3496

'this' est toujours capturé par valeur : '&' ignoré

Vous ne pouvez pas capturer le pointeur `this` par référence.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Capturez le pointeur `this` par valeur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3496, car une référence au pointeur `this` se trouve dans la liste de capture d’une expression lambda :

```cpp
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
