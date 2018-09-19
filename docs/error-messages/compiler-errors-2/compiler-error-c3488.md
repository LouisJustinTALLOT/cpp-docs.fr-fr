---
title: Erreur du compilateur C3488 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3488
dev_langs:
- C++
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15e1a21781eed96ee3a2a1430da8e43013393912
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061787"
---
# <a name="compiler-error-c3488"></a>Erreur du compilateur C3488

'var' n’est pas autorisé quand le mode de capture par défaut est par référence

Quand vous spécifiez que le mode de capture par défaut d’une expression lambda est par référence, vous ne pouvez pas passer une variable par référence à la clause de capture de cette expression.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Ne passez pas explicitement la variable à la clause de capture.

- Ne spécifiez pas le mode de capture par défaut par référence.

- Spécifiez le mode de capture par défaut par valeur.

- Passez la variable par valeur à la clause de capture. (Cela peut modifier le comportement de l’expression lambda.)

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3488, car une référence à la variable `n` apparaît dans la clause de capture d’une expression lambda dont le mode par défaut est par référence :

```
// C3488a.cpp

int main()
{
   int n = 5;
   [&, &n]() { return n; } (); // C3488
}
```

## <a name="example"></a>Exemple

L’exemple suivant illustre quatre résolutions possibles de l’erreur C3488 :

```
// C3488b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass &n to the capture clause.
   [&]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-reference as the default capture mode.
   [&n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-value as the default capture mode.
   [=, &n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by value to the capture clause.
   [n]() { return n; } ();
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)