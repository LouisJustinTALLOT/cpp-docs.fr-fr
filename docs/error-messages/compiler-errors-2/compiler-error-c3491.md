---
title: Erreur du compilateur C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: 78f90ee1c44a0d42e529a027b1e7fc90a0da3cdb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738321"
---
# <a name="compiler-error-c3491"></a>Erreur du compilateur C3491

'variable' : impossible de modifier une capture par valeur dans une expression lambda non mutable

Une expression lambda non mutable ne peut pas modifier la valeur d’une variable capturée par valeur.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Déclarez votre expression lambda avec le mot clé `mutable` , ou

- Passez la variable par référence à la liste de capture de l’expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3491, car le corps d’une expression lambda non mutable modifie la variable de capture `m`:

```cpp
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>Exemple

L’exemple suivant résout l’erreur C3491 en déclarant l’expression lambda avec le mot clé `mutable` :

```cpp
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
