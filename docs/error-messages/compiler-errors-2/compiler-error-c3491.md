---
title: Erreur du compilateur C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: 12f50e48fc18fc23d078b6dbc7d21d05efa06d43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381083"
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