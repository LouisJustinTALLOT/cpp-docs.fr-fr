---
description: 'En savoir plus sur : erreur du compilateur C3499'
title: Erreur du compilateur C3499
ms.date: 11/04/2016
f1_keywords:
- C3499
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
ms.openlocfilehash: e4e572be1b5e39ccec6bf1ca64eaf62a3e44ef28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315476"
---
# <a name="compiler-error-c3499"></a>Erreur du compilateur C3499

une expression lambda dont le type de retour spécifié est void ne peut pas retourner de valeur

Le compilateur génère cette erreur lorsqu’une expression lambda qui spécifie **`void`** comme type de retour retourne une valeur, ou lorsqu’une expression lambda contient plusieurs instructions et retourne une valeur, mais ne spécifie pas son type de retour.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Ne retournez pas une valeur à partir de l’expression lambda ; ou

- Fournissez le type de retour de l’expression lambda ; ou

- Combinez les instructions qui composent le corps de l’expression lambda dans une instruction unique.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’erreur C3499, car le corps d’une expression lambda contient plusieurs instructions et retourne une valeur, mais l’expression lambda ne spécifie pas le type de retour :

```cpp
// C3499a.cpp

int main()
{
   [](int x) { int n = x * 2; return n; } (5); // C3499
}
```

L’exemple suivant montre deux résolutions possibles pour l’erreur C3499. La première résolution fournit le type de retour de l’expression lambda. La seconde résolution combine les instructions qui composent le corps de l’expression lambda dans une instruction unique.

```cpp
// C3499b.cpp

int main()
{
   // Possible resolution 1:
   // Provide the return type of the lambda expression.
   [](int x) -> int { int n = x * 2; return n; } (5);

   // Possible resolution 2:
   // Combine the statements that make up the body of
   // the lambda expression into a single statement.
   [](int x) { return x * 2; } (5);
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
