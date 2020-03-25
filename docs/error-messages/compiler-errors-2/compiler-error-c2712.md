---
title: Erreur du compilateur C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: a25c59fa5c9ba0102666f6c8922a61b063e7627a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202304"
---
# <a name="compiler-error-c2712"></a>Erreur du compilateur C2712

> impossible d'utiliser __try dans les fonctions nécessitant un déroulement d'objet

## <a name="remarks"></a>Notes

Une erreur C2712 peut se produire si vous utilisez [/EHsc](../../build/reference/eh-exception-handling-model.md)et qu’une fonction avec gestion structurée des exceptions possède également des objets qui nécessitent un déroulement (destruction).

Solutions possibles :

- Déplacez le code nécessitant la gestion structurée des exceptions vers une autre fonction.

- Réécrivez les fonctions qui utilisent la gestion structurée des exceptions pour éviter l'utilisation de variables locales et de paramètres possédant des destructeurs. N'utilisez pas la gestion structurée des exceptions dans les constructeurs ni les destructeurs.

- Compilez sans /EHsc.

Une erreur C2712 peut également se produire si vous appelez une méthode déclarée à l’aide du mot clé [__event](../../cpp/event.md) . Étant donné que l’événement peut être utilisé dans un environnement multithread, le compilateur génère du code qui empêche la manipulation de l’objet événement sous-jacent, puis il encadre le code généré dans une [instruction try-finally](../../cpp/try-finally-statement.md)SEH. Par conséquent, l’erreur C2712 se produit si vous appelez la méthode d’événement et passez par valeur un argument dont le type possède un destructeur. Dans ce cas, une solution consiste à passer l'argument en tant que référence constante.

C2712 peut également se produire si vous compilez avec **/clr : pure** et déclarez un tableau statique de pointeurs vers des fonctions dans un bloc `__try`. Un membre statique requiert que le compilateur utilise l’initialisation dynamique sous **/clr : pure**, ce qui C++ implique la gestion des exceptions. Toutefois, la gestion des exceptions C++ n'est pas autorisée dans un bloc `__try`.

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

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
