---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4838'
title: Avertissement du compilateur (niveau 1) C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: 2676ef05934ee3c5e6afbf6df8d6d7a306db68ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197958"
---
# <a name="compiler-warning-level-1-c4838"></a>Avertissement du compilateur (niveau 1) C4838

la conversion de’type_1 'en’type_2 'requiert une conversion restrictive

Une conversion restrictive implicite a été trouvée lors de l’utilisation de l’initialisation d’agrégat ou de liste.

Le langage C permet des conversions restrictives implicites dans les assignations et l’initialisation, et C++ suit la fonction, même si la réduction inattendue est une cause de nombreuses erreurs de code. Pour rendre le code plus sécurisé, la norme C++ requiert un message de diagnostic quand une conversion restrictive se produit dans une liste d’initialisation. Dans Visual C++, le diagnostic est une [Erreur du compilateur C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) lors de l’utilisation de la syntaxe d’initialisation uniforme prise en charge à compter de Visual Studio 2015. Le compilateur génère un avertissement C4838 lors de l’utilisation de la syntaxe d’initialisation de liste ou d’agrégat prise en charge par Visual Studio 2013.

Une conversion restrictive peut être possible lorsque vous savez que la plage possible de valeurs converties peut tenir dans la cible. Dans ce cas, vous en connaissez davantage que le compilateur. Si vous effectuez une conversion restrictive intentionnellement, rendez vos intentions explicites à l’aide d’un cast statique. Dans le cas contraire, ce message d’avertissement indique presque toujours que vous avez un bogue dans votre code. Vous pouvez résoudre le problème en vous assurant que les objets que vous initialisez ont des types suffisamment grands pour gérer les entrées.

L’exemple suivant génère C4838 et montre une façon de le résoudre :

```cpp
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
