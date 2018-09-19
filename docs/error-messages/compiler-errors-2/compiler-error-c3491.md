---
title: Erreur du compilateur C3491 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3491
dev_langs:
- C++
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64d7b2e4bd602a53afeba2f77293c31bb28902d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068765"
---
# <a name="compiler-error-c3491"></a>Erreur du compilateur C3491

'variable' : impossible de modifier une capture par valeur dans une expression lambda non mutable

Une expression lambda non mutable ne peut pas modifier la valeur d’une variable capturée par valeur.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Déclarez votre expression lambda avec le mot clé `mutable` , ou

- Passez la variable par référence à la liste de capture de l’expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3491, car le corps d’une expression lambda non mutable modifie la variable de capture `m`:

```
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>Exemple

L’exemple suivant résout l’erreur C3491 en déclarant l’expression lambda avec le mot clé `mutable` :

```
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)