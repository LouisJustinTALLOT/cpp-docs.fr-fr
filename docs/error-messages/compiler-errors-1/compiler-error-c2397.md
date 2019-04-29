---
title: Erreur du compilateur C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 61f23269e0b6ed65a485f11e49e492d2248b8a42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378932"
---
# <a name="compiler-error-c2397"></a>Erreur du compilateur C2397

conversion de 'type_1' en 'type_2' requiert une conversion restrictive

Une conversion restrictive implicite a été trouvée lors de l’utilisation d’initialisation uniforme.

Le langage C permet les conversions restrictives implicites dans les assignations et d’initialisation et C++ suit la couleur, même si les conversions restrictives inattendue sont une cause de nombreuses erreurs de code. Pour rendre le code plus sûr, la norme C++ nécessite un message de diagnostic lorsqu’une conversion restrictive se produit dans une liste d’initialisation. Dans Visual C++, le diagnostic est Erreur du compilateur C2397 lorsque vous utilisez le début de la syntaxe prise en charge d’initialisation uniforme dans Visual Studio 2015. Le compilateur génère [Avertissement du compilateur (niveau 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) lors de l’utilisation de la liste ou la syntaxe de l’initialisation d’agrégats pris en charge par Visual Studio 2013.

Une conversion restrictive peut être OK lorsque vous savez que la plage de valeurs converties possible peut être contenue dans la cible. Dans ce cas, vous savez plus que le compilateur effectue. Si vous effectuez une conversion restrictive intentionnellement, rendre vos intentions explicite à l’aide d’un cast statique. Sinon, ce message d’erreur indique presque toujours qu'avoir un bogue dans votre code. Vous pouvez le résoudre en vous assurant que les objets que vous initialisez ont des types qui sont assez grandes pour gérer les entrées.

L’exemple suivant génère C2397 et montre une façon de résoudre le problème :

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