---
description: 'En savoir plus sur : erreur du compilateur C3496'
title: Erreur du compilateur C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: dc3160e1007b65b70ea952aeaee3c77ba8ab21e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315515"
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
