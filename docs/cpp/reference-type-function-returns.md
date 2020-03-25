---
title: Retours de fonction de type référence
ms.date: 11/04/2016
helpviewer_keywords:
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
ms.openlocfilehash: 5e84643713dcbcb278fe7ce07c5d55f3593ec2ef
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188296"
---
# <a name="reference-type-function-returns"></a>Retours de fonction de type référence

Les fonctions peuvent être déclarées pour retourner un type référence. Il existe deux raisons d'effectuer une déclaration :

- Les informations retournées sont un objet suffisamment grand pour que retourner une référence soit plus efficace que retourner une copie.

- Le type de la fonction doit être une l-value.

- L'objet référencé ne sort pas de la portée lors du retour de la fonction.

Tout comme il peut être plus efficace de passer des objets volumineux *à* des fonctions par référence, il peut également être plus efficace de retourner *des objets volumineux à partir de* fonctions par référence. Le protocole de retour par référence élimine le besoin de copier l'objet dans un emplacement temporaire avant de le retourner.

Les types de retour par référence peuvent également être utiles lorsque la fonction doit prendre une l-value. La plupart des opérateurs surchargés appartiennent à cette catégorie, notamment l'opérateur d'assignation. Les opérateurs surchargés sont couverts par les [opérateurs surchargés](../cpp/operator-overloading.md).

## <a name="example"></a>Exemple

Prenons l'exemple de `Point` :

```cpp
// refType_function_returns.cpp
// compile with: /EHsc

#include <iostream>
using namespace std;

class Point
{
public:
// Define "accessor" functions as
//  reference types.
unsigned& x();
unsigned& y();
private:
// Note that these are declared at class scope:
unsigned obj_x;
unsigned obj_y;
};

unsigned& Point :: x()
{
return obj_x;
}
unsigned& Point :: y()
{
return obj_y;
}

int main()
{
Point ThePoint;
// Use x() and y() as l-values.
ThePoint.x() = 7;
ThePoint.y() = 9;

// Use x() and y() as r-values.
cout << "x = " << ThePoint.x() << "\n"
<< "y = " << ThePoint.y() << "\n";
}
```

## <a name="output"></a>Output

```Output
x = 7
y = 9
```

Notez que les fonctions `x` et `y` sont déclarées comme retournant des types référence. Ces fonctions peuvent être utilisées des deux côtés d'une instruction d'assignation.

Notez également que, dans main, l'objet Point reste dans la portée et ses membres de référence sont par conséquent toujours actifs et accessibles en toute sécurité.

Les déclarations des types référence doivent contenir des initialiseurs sauf dans les cas suivants :

- Déclaration **extern** explicite

- Déclaration d'une classe membre

- Déclaration sans classe

- Déclaration d’un argument d’une fonction ou du type de retour pour une fonction

## <a name="caution-returning-address-of-local"></a>Attention en retournant l'adresse d'une variable locale

Si vous déclarez un objet dans la portée locale, cet objet sera détruit lors du retour de la fonction. Si la fonction retourne une référence à cet objet, cette référence est susceptible de provoquer une violation d'accès lors de l'exécution si l'appelant tente d'utiliser la référence null.

```cpp
// C4172 means Don’t do this!!!
Foo& GetFoo()
{
    Foo f;
    ...
    return f;
} // f is destroyed here
```

Dans ce cas, le compilateur émet un avertissement : `warning C4172: returning address of local variable or temporary`. Dans des programmes simples, il est possible qu'occasionnellement aucune violation d'accès ne se produise si la référence est accessible par l'appelant avant le remplacement de l'emplacement de mémoire. C'est le fruit du hasard. Tenez compte de l'avertissement.

## <a name="see-also"></a>Voir aussi

[Informations de référence](../cpp/references-cpp.md)
