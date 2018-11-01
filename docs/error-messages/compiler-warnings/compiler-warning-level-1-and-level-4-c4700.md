---
title: Avertissement du compilateur (niveaux 1 et 4) C4700
ms.date: 02/21/2018
f1_keywords:
- C4700
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
ms.openlocfilehash: fa3326bd5ab495dbc4c54130bb168422eb827dce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463217"
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>Avertissement du compilateur (niveaux 1 et 4) C4700

> variable locale non initialisée '*nom*' utilisé

La variable locale *nom* a été *utilisé*, autrement dit, lecture, avant qu’il ait été attribuée une valeur. En C et C++, les variables locales ne sont pas initialisées par défaut. Variables non initialisées peuvent contenir n’importe quelle valeur, et leur utilisation entraîne un comportement non défini. Avertissement C4700 indique presque toujours un bogue qui peut entraîner des résultats imprévisibles ou se bloque dans votre programme.

Pour résoudre ce problème, vous pouvez initialiser des variables locales quand elles sont déclarées ou leur attribuer une valeur avant de les utiliser. Une fonction peut être utilisée pour initialiser une variable qui est passé comme paramètre de référence, ou quand son adresse est passée comme un paramètre de pointeur.

## <a name="example"></a>Exemple

Cet exemple génère l’erreur C4700 lorsque variables t, u et v sont utilisés avant qu’ils sont initialisés et affiche le type de valeur de mémoire peut entraîner. Variables x, y et z ne pas provoquer l’avertissement, car ils sont initialisés avant leur utilisation :

```cpp
// c4700.cpp
// compile by using: cl /EHsc /W4 c4700.cpp
#include <iostream>

// function takes an int reference to initialize
void initialize(int& i)
{
    i = 21;
}

int main()
{
    int s, t, u, v;   // Danger, uninitialized variables

    s = t + u + v;    // C4700: t, u, v used before initialization
    std::cout << "Value in s: " << s << std::endl;

    int w, x;         // Danger, uninitialized variables
    initialize(x);    // fix: call function to init x before use
    int y{10};        // fix: initialize y, z when declared
    int z{11};        // This C++11 syntax is recommended over int z = 11;

    w = x + y + z;    // Okay, all values initialized before use
    std::cout << "Value in w: " << w << std::endl;
}
```

Lorsque ce code est exécution, t, u et v n’est pas initialisées, et la sortie de s est imprévisible :

```Output
Value in s: 37816963
Value in w: 42
```
