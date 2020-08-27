---
title: Erreur du compilateur C2712
description: Décrit l’erreur C2712 du compilateur Microsoft C/C++.
ms.date: 08/25/2020
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: 2f0b883607241473a429919e06de9e975fa2e3c1
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898702"
---
# <a name="compiler-error-c2712"></a>Erreur du compilateur C2712

> Impossible `__try` d’utiliser dans les fonctions qui requièrent le déroulement de l’objet

## <a name="remarks"></a>Notes

Une erreur C2712 peut se produire si vous utilisez [`/EHsc`](../../build/reference/eh-exception-handling-model.md) , et une fonction avec gestion structurée des exceptions a également des objets qui nécessitent un déroulement (destruction).

Solutions possibles :

- Déplacez le code nécessitant la gestion structurée des exceptions vers une autre fonction.

- Réécrivez les fonctions qui utilisent la gestion structurée des exceptions pour éviter l'utilisation de variables locales et de paramètres possédant des destructeurs. N'utilisez pas la gestion structurée des exceptions dans les constructeurs ni les destructeurs.

- Compilez sans /EHsc.

Une erreur C2712 peut également se produire si vous appelez une méthode déclarée à l’aide du [`__event`](../../cpp/event.md) mot clé. Étant donné que l’événement peut être utilisé dans un environnement multithread, le compilateur génère du code qui empêche la manipulation de l’objet événement sous-jacent, puis il encadre le code généré dans une [ `try-finally` instruction](../../cpp/try-finally-statement.md)SEH. Par conséquent, l’erreur C2712 se produit si vous appelez la méthode d’événement et passez par valeur un argument dont le type possède un destructeur. Dans ce cas, une solution consiste à passer l'argument en tant que référence constante.

C2712 peut également se produire si vous compilez avec **`/clr:pure`** et déclarez un tableau statique de pointeurs vers des fonctions dans un **`__try`** bloc. Un membre statique requiert que le compilateur utilise l’initialisation dynamique sous **`/clr:pure`** , ce qui implique la gestion des exceptions C++. Toutefois, la gestion des exceptions C++ n’est pas autorisée dans un **`__try`** bloc.

Les **`/clr:pure`** **`/clr:safe`** Options du compilateur et sont dépréciées dans visual studio 2015 et ne sont pas prises en charge dans visual studio 2017.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2712 et montre comment la corriger.

```cpp
// C2712.cpp
// compile with: /clr:pure /c
struct S1 {
   static int smf();
   void fnc();
};

void S1::fnc() {
   __try {
      static int (*array_1[])() = {smf,};   // C2712

      // OK
      static int (*array_2[2])();
      array_2[0] = smf;
    }
    __except(0) {}
}
```
