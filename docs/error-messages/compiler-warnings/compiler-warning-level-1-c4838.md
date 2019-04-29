---
title: Compilateur Warning (level 1) C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: dcb7062c751320a9f9c612b42caf6d018047d8d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380836"
---
# <a name="compiler-warning-level-1-c4838"></a>Compilateur Warning (level 1) C4838

conversion de 'type_1' en 'type_2' requiert une conversion restrictive

Une conversion restrictive implicite a été trouvée lors de l’utilisation de l’initialisation d’agrégat ou de liste.

Le langage C permet les conversions restrictives implicites dans les assignations et d’initialisation et C++ suit la couleur, même si les conversions restrictives inattendue sont une cause de nombreuses erreurs de code. Pour rendre le code plus sûr, la norme C++ nécessite un message de diagnostic lorsqu’une conversion restrictive se produit dans une liste d’initialisation. Dans Visual C++, le diagnostic est [erreur du compilateur C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) lors de l’utilisation de la syntaxe d’initialisation uniforme pris en charge à compter de Visual Studio 2015. Le compilateur génère l’avertissement C4838 lors de l’utilisation de la liste ou la syntaxe de l’initialisation d’agrégats pris en charge par Visual Studio 2013.

Une conversion restrictive peut être OK lorsque vous savez que la plage de valeurs converties possible peut être contenue dans la cible. Dans ce cas, vous savez plus que le compilateur effectue. Si vous effectuez une conversion restrictive intentionnellement, rendre vos intentions explicite à l’aide d’un cast statique. Sinon, ce message d’avertissement indique presque toujours que vous disposez d’un bogue dans votre code. Vous pouvez le résoudre en vous assurant que les objets que vous initialisez ont des types qui sont assez grandes pour gérer les entrées.

L’exemple suivant génère C4838 et montre une façon de résoudre le problème :

```
// C4838.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C4838.cpp

struct S1 {
    int m1;
    double m2, m3;
};

void function_C4838(double d1) {
    double ad[] = { 1, d1 }; // OK
    int ai[] = { 1, d1 };    // warning C4838
    S1 s11 = { 1, 2, d1 };   // OK
    S1 s12 { d1, 2, 3 };     // warning C4838
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838
}
```