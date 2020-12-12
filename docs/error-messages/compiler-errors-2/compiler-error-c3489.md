---
description: 'En savoir plus sur : erreur du compilateur C3489'
title: Erreur du compilateur C3489
ms.date: 11/04/2016
f1_keywords:
- C3489
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
ms.openlocfilehash: 658fc83476a9fe6f0db3ac27f44a05e1cb1d0c28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315643"
---
# <a name="compiler-error-c3489"></a>Erreur du compilateur C3489

'var' est obligatoire lorsque le mode de capture par défaut est le mode par valeur

Quand vous spécifiez que le mode de capture par défaut d’une expression lambda est par valeur, vous ne pouvez pas passer une variable par valeur à la clause de capture de cette expression.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Ne passez pas explicitement la variable à la clause de capture.

- Ne spécifiez pas le mode de capture par valeur comme mode par défaut.

- Spécifiez le mode de capture par référence comme mode par défaut.

- Passez la variable par référence à la clause de capture. (Cela peut modifier le comportement de l’expression lambda.)

## <a name="examples"></a>Exemples

L’exemple suivant génère l’erreur C3489 car la variable `n` apparaît par valeur dans la clause de capture d’une expression lambda dont le mode par défaut est par valeur :

```cpp
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

L’exemple suivant illustre quatre résolutions possibles de l’erreur C3489 :

```cpp
// C3489b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass n to the capture clause.
   [=]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-value as the default capture mode.
   [n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-reference as the default capture mode.
   [&, n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by reference to the capture clause.
   [&n]() { return n; } ();
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
