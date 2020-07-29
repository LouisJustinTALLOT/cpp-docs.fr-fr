---
title: Erreur du compilateur C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 993d391f28a59afc8926748f2e6f34ab441657dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228854"
---
# <a name="compiler-error-c3496"></a>Erreur du compilateur C3496

'this' est toujours capturé par valeur : '&' ignoré

Vous ne pouvez pas capturer le **`this`** pointeur par référence.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Capturez le **`this`** pointeur par valeur.

## <a name="example"></a>Exemple

L’exemple suivant génère C3496, car une référence au **`this`** pointeur apparaît dans la liste de capture d’une expression lambda :

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
