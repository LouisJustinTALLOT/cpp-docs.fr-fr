---
title: Erreur du compilateur C3495 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3495
dev_langs:
- C++
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dda1e2f2699969ad0bc446d9f79a0004e043998d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067387"
---
# <a name="compiler-error-c3495"></a>Erreur du compilateur C3495

'var' : une capture lambda doit avoir une durée de stockage automatique

Vous ne pouvez pas capturer une variable qui n’a pas de durée de stockage automatique, telle qu’une variable qui est marquée `static` ou `extern`.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Ne passez pas une variable `static` ni `extern` à la liste de capture de l’expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3495, car la variable `static` `n` figure dans la liste de capture d’une expression lambda :

```
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)


