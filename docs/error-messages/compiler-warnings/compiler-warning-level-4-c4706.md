---
title: Compilateur avertissement (niveau 4) C4706 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4706
dev_langs:
- C++
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 843edeaf490f27475003e9303f7929b818e2b104
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036954"
---
# <a name="compiler-warning-level-4-c4706"></a>Avertissement du compilateur (niveau 4) C4706

assignation au sein d’une expression conditionnelle

La valeur de test dans une expression conditionnelle était le résultat d’une assignation.

Une affectation a la valeur (la valeur sur le côté gauche de l’assignation) qui peut être légalement utilisée dans une autre expression, y compris une expression de test.

L’exemple suivant génère l’erreur C4706 :

```
// C4706a.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a  = b ) // C4706
   {
   }
}
```

L’avertissement se produit même si vous doublez les parenthèses autour de la condition de test :

```
// C4706b.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a  =  b ) ) // C4706
   {
   }
}
```

Si votre intention est de tester une relation et non ne pas d’effectuer une assignation, utilisez le `==` opérateur. Par exemple, la ligne suivante tests si un et b sont égaux :

```
// C4706c.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a == b )
   {
   }
}
```

Si vous souhaitez que votre test de valeur au résultat d’une assignation, un test pour vous assurer que l’assignation est différente de zéro ou non null. Par exemple, le code suivant génère pas cet avertissement :

```
// C4706d.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a = b ) != 0 )
   {
   }
}
```