---
title: Erreur du compilateur C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: eff7c7a4f39524aa1d894b7b4590aa809714aae6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041200"
---
# <a name="compiler-error-c3481"></a>Erreur du compilateur C3481

'var' : variable de capture lambda introuvable

Le compilateur n’a pas pu trouver la définition d’une variable que vous avez transmise à la liste de capture d’une expression lambda.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez la variable de la liste de capture de l’expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3481, car la variable `n` n’est pas définie :

```
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)