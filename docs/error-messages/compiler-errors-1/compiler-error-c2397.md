---
title: C2397 d’erreur du compilateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- C2397
dev_langs:
- C++
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9d080450368618cc874de0ae96209e547847f8c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196881"
---
# <a name="compiler-error-c2397"></a>C2397 d’erreur du compilateur
la conversion de 'type_1' en 'type_2' requiert une conversion restrictive  
  
 Une conversion restrictive implicite a été trouvée lors de l’utilisation de l’initialisation uniforme.  
  
 Le langage C permet les conversions restrictives implicites dans les assignations et d’initialisation et C++ suit la couleur, même si restrictives inattendu sont une cause de nombreuses erreurs de code. Pour rendre le code plus sûre, la norme C++ requiert un message de diagnostic lorsqu’une conversion restrictive se produit dans une liste d’initialisation. Dans Visual C++, le diagnostic est C2397 d’erreur du compilateur lors de l’utilisation du début de la syntaxe prise en charge l’initialisation uniforme dans Visual Studio 2015. Le compilateur génère [C4838 d’avertissement du compilateur (niveau 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) lors de l’utilisation de la liste ou la syntaxe de l’initialisation d’agrégats pris en charge par Visual Studio 2013.  
  
 Une conversion restrictive peut être OK lorsque vous savez que la plage possible de valeurs converties peut être contenue dans la cible. Dans ce cas, vous savez plus que le compilateur effectue. Si vous effectuez une conversion restrictive intentionnellement, rendre vos intentions explicite à l’aide d’un cast statique. Dans le cas contraire, ce message d’erreur indique presque toujours qu'avoir un bogue dans votre code. Vous pouvez résoudre ce problème en vous assurant que les objets que vous initialisez ont des types qui sont assez grandes pour gérer les entrées.  
  
 L’exemple suivant génère C2397 et illustre une façon de pour résoudre ce problème :  
  
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