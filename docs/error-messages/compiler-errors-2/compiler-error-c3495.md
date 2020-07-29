---
title: Erreur du compilateur C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: a67d4d859e3a9dd2241f14a476492df0fd3e6b8d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223419"
---
# <a name="compiler-error-c3495"></a>Erreur du compilateur C3495

'var' : une capture lambda doit avoir une durée de stockage automatique

Vous ne pouvez pas capturer une variable qui n’a pas de durée de stockage automatique, telle qu’une variable marquée **`static`** ou **`extern`** .

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Ne transmettez pas **`static`** de **`extern`** variable ou à la liste de capture de l’expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère C3495, car la **`static`** variable `n` apparaît dans la liste de capture d’une expression lambda :

```cpp
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
