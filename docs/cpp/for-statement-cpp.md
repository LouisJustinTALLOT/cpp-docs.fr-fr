---
title: for, instruction (C++)
description: Référence à l’instruction C++ standard for dans Microsoft Visual Studio C++.
f1_keywords:
- for_cpp
ms.date: 04/14/2020
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: 16486fd58a9b3fec750ebef6ec6647f9d92bca3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231180"
---
# <a name="for-statement-c"></a>for, instruction (C++)

Exécute une instruction à plusieurs reprises jusqu'à ce que la condition soit false. Pour plus d’informations sur l’instruction for basée sur une plage, consultez [instruction for basée sur une plage (C++)](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Syntaxe

> **`for (`***init-expression* **`;`** *cond-expression* **`;`** *loop-expression***`)`**\
> &nbsp;&nbsp;&nbsp;&nbsp;_gestion_**`;`**

## <a name="remarks"></a>Notes

Utilisez l' **`for`** instruction pour construire des boucles qui doivent s’exécuter un nombre de fois spécifié.

L' **`for`** instruction se compose de trois parties facultatives, comme indiqué dans le tableau suivant.

### <a name="for-loop-elements"></a>Éléments de boucle For

|Nom de la syntaxe|Moment de l'exécution|Description|
|-----------------|-------------------|-----------------|
|`init-expression`|Avant tout autre élément de l' **`for`** instruction, `init-expression` n’est exécuté qu’une seule fois. Le contrôle passe alors à `cond-expression`.|Souvent employé pour initialiser des index de boucle. Elle peut contenir des expressions ou des déclarations.|
|`cond-expression`|Avant l'exécution de chaque itération de `statement`, y compris la première itération. `statement` est exécuté uniquement si `cond-expression` a la valeur true (valeur différente de zéro).|Expression qui correspond à un type intégral ou à un type de classe avec une conversion non ambiguë en type intégral. Normalement utilisée pour déterminer les critères d'arrêts de boucles.|
|`loop-expression`|À la fin de chaque itération de `statement`. `loop-expression` est évalué après l'exécution de `cond-expression`.|Normalement utilisée pour incrémenter les index de boucle.|

Les exemples suivants illustrent différentes façons d’utiliser l' **`for`** instruction.

```cpp
#include <iostream>
using namespace std;

int main() {
    // The counter variable can be declared in the init-expression.
    for (int i = 0; i < 2; i++ ){
       cout << i;
    }
    // Output: 01
    // The counter variable can be declared outside the for loop.
    int i;
    for (i = 0; i < 2; i++){
        cout << i;
    }
    // Output: 01
    // These for loops are the equivalent of a while loop.
    i = 0;
    while (i < 2){
        cout << i++;
    }
}
    // Output: 012
```

`init-expression` et `loop-expression` peuvent contenir plusieurs instructions séparées par des virgules. Par exemple :

```cpp
#include <iostream>
using namespace std;

int main(){
    int i, j;
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {
        cout << "i + j = " << (i + j) << '\n';
    }
}
    // Output:
    i + j = 15
    i + j = 17
    i + j = 19
```

`loop-expression` peut être incrémenté ou décrémenté, ou autrement modifié.

```cpp
#include <iostream>
using namespace std;

int main(){
for (int i = 10; i > 0; i--) {
        cout << i << ' ';
    }
    // Output: 10 9 8 7 6 5 4 3 2 1
    for (int i = 10; i < 20; i = i+2) {
        cout << i << ' ';
    }
    // Output: 10 12 14 16 18
```

Une **`for`** boucle se termine lorsqu’une instruction [break](../cpp/break-statement-cpp.md), [Return](../cpp/return-statement-cpp.md)ou [goto](../cpp/goto-statement-cpp.md) (vers une instruction étiquetée à l’extérieur de la **`for`** boucle) `statement` est exécutée. Une instruction [continue](../cpp/continue-statement-cpp.md) dans une **`for`** boucle ne termine que l’itération en cours.

Si `cond-expression` est omis, il est pris **`true`** en compte et la **`for`** boucle ne se termine pas sans **`break`** , **`return`** ou **`goto`** dans `statement` .

Bien que les trois champs de l' **`for`** instruction soient normalement utilisés pour l’initialisation, le test de fin et l’incrémentation, ils ne sont pas limités à ces utilisations. Par exemple, le code suivant affiche les nombres 0 à 4. Dans ce cas, `statement` est l'instruction null :

```cpp
#include <iostream>
using namespace std;

int main()
{
    int i;
    for( i = 0; i < 5; cout << i << '\n', i++){
        ;
    }
}
```

## <a name="for-loops-and-the-c-standard"></a>Boucles for et norme C++

La norme C++ indique qu’une variable déclarée dans une **`for`** boucle doit sortir de la portée après la fin de la **`for`** boucle. Par exemple :

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

Par défaut, sous [/Ze](../build/reference/za-ze-disable-language-extensions.md), une variable déclarée dans une **`for`** boucle reste dans la portée jusqu’à la fin de la **`for`** portée englobante de la boucle.

[/Zc : forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) active le comportement standard des variables déclarées dans les boucles for sans avoir à spécifier `/Za` .

Il est également possible d’utiliser les différences de portée de la **`for`** boucle pour redéclarer les variables sous `/Ze` comme suit :

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

Ce comportement reproduit plus fidèlement le comportement standard d’une variable déclarée dans une **`for`** boucle, ce qui nécessite que les variables déclarées dans une **`for`** boucle soient hors de portée une fois la boucle terminée. Lorsqu’une variable est déclarée dans une **`for`** boucle, le compilateur la promeut en interne vers une variable locale dans la **`for`** portée englobante de la boucle. Elle est promue même s’il existe déjà une variable locale portant le même nom.

## <a name="see-also"></a>Voir aussi

[Instructions d'itération](../cpp/iteration-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[while, instruction (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while, instruction (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Basé sur une plage, instruction (C++)](../cpp/range-based-for-statement-cpp.md)
