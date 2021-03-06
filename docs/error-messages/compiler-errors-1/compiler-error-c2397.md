---
description: 'En savoir plus sur : erreur du compilateur C2397'
title: Erreur du compilateur C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 8e5f000b8d0881fd6a57bb4895afbdef0e7c598a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145377"
---
# <a name="compiler-error-c2397"></a>Erreur du compilateur C2397

la conversion de’type_1 'en’type_2 'requiert une conversion restrictive

Une conversion restrictive implicite a été trouvée lors de l’utilisation de l’initialisation uniforme.

Le langage C permet des conversions restrictives implicites dans les assignations et l’initialisation, et C++ suit la fonction, même si la réduction inattendue est une cause de nombreuses erreurs de code. Pour rendre le code plus sécurisé, la norme C++ requiert un message de diagnostic quand une conversion restrictive se produit dans une liste d’initialisation. Dans Visual C++, le diagnostic est une erreur du compilateur C2397 lors de l’utilisation de la syntaxe d’initialisation uniforme prise en charge à compter de Visual Studio 2015. Le compilateur génère un [Avertissement du compilateur (niveau 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) lors de l’utilisation de la syntaxe d’initialisation de liste ou d’agrégat prise en charge par Visual Studio 2013.

Une conversion restrictive peut être possible lorsque vous savez que la plage possible de valeurs converties peut tenir dans la cible. Dans ce cas, vous en connaissez davantage que le compilateur. Si vous effectuez une conversion restrictive intentionnellement, rendez vos intentions explicites à l’aide d’un cast statique. Dans le cas contraire, ce message d’erreur indique presque toujours que vous avez un bogue dans votre code. Vous pouvez résoudre le problème en vous assurant que les objets que vous initialisez ont des types suffisamment grands pour gérer les entrées.

L’exemple suivant génère C2397 et montre une façon de le résoudre :

```
// C2397.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C2397.cpp
#include <vector>

struct S1 {
    int m1;
    double m2, m3;
};

void function_C2397(double d1) {
    char c1 { 127 };          // OK
    char c2 { 513 };          // error C2397

    std::vector<S1> vS1;
    vS1.push_back({ d1, 2, 3 }); // error C2397

    // Possible fix if you know d1 always fits in an int
    vS1.push_back({ static_cast<int>(d1), 2, 3 });
}
```
