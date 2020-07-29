---
title: Erreur du compilateur C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: f6f20d9af424fdd4254fc15e0580d62b9dfba144
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184473"
---
# <a name="compiler-error-c3491"></a>Erreur du compilateur C3491

'variable' : impossible de modifier une capture par valeur dans une expression lambda non mutable

Une expression lambda non mutable ne peut pas modifier la valeur d’une variable capturée par valeur.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Déclarez votre expression lambda avec le **`mutable`** mot clé, ou

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

L’exemple suivant résout C3491 en déclarant l’expression lambda avec le **`mutable`** mot clé :

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
