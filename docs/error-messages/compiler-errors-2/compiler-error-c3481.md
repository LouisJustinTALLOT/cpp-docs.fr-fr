---
description: 'En savoir plus sur : erreur du compilateur C3481'
title: Erreur du compilateur C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: 31f13b56a2b5df66a5765ee63313ffe265c15fe4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113400"
---
# <a name="compiler-error-c3481"></a>Erreur du compilateur C3481

'var' : variable de capture lambda introuvable

Le compilateur n’a pas pu trouver la définition d’une variable que vous avez transmise à la liste de capture d’une expression lambda.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez la variable de la liste de capture de l’expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3481, car la variable `n` n’est pas définie :

```cpp
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
