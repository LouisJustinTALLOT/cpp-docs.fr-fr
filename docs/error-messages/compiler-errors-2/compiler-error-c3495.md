---
description: 'En savoir plus sur : erreur du compilateur C3495'
title: Erreur du compilateur C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 3c04c80182dad32b539e09224fd9e303b3325578
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113166"
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
