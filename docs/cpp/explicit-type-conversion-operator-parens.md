---
description: 'En savoir plus sur : opérateur de conversion de type explicite : ()'
title: 'Opérateur de conversions de type explicite : ()'
ms.date: 11/04/2016
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
ms.openlocfilehash: cb2a1ff742b71edf2f298512a55ab37dd3d37f77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273382"
---
# <a name="explicit-type-conversion-operator-"></a>Opérateur de conversions de type explicite : ()

C++ permet de convertir en type explicite à l'aide d'une syntaxe similaire à la syntaxe de l'appel de fonction.

## <a name="syntax"></a>Syntaxe

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>Notes

Un *simple-type-name* suivi d’une *expression-List* placée entre parenthèses construit un objet du type spécifié à l’aide des expressions spécifiées. L'exemple suivant montre une conversion de type explicite en type int :

```cpp
int i = int( d );
```

L’exemple suivant illustre une `Point` classe.

## <a name="example"></a>Exemple

```cpp
// expre_Explicit_Type_Conversion_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
public:
    // Define default constructor.
    Point() { _x = _y = 0; }
    // Define another constructor.
    Point( int X, int Y ) { _x = X; _y = Y; }

    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
    void Show()   { cout << "x = " << _x << ", "
                         << "y = " << _y << "\n"; }
private:
    unsigned _x;
    unsigned _y;
};

int main()
{
    Point Point1, Point2;

    // Assign Point1 the explicit conversion
    //  of ( 10, 10 ).
    Point1 = Point( 10, 10 );

    // Use x() as an l-value by assigning an explicit
    //  conversion of 20 to type unsigned.
    Point1.x() = unsigned( 20 );
    Point1.Show();

    // Assign Point2 the default Point object.
    Point2 = Point();
    Point2.Show();
}
```

## <a name="output"></a>Output

```Output
x = 20, y = 10
x = 0, y = 0
```

Bien que l'exemple précédent montre la conversion de type explicite à l'aide de constantes, la même technique fonctionne pour exécuter ces conversions sur des objets. Le fragment de code suivant illustre ceci :

```cpp
int i = 7;
float d;

d = float( i );
```

Les conversions de types explicites peuvent également être spécifiées en utilisant la syntaxe du cast. L'exemple précédent, réécrit à l'aide de la syntaxe du cast, est :

```cpp
d = (float)i;
```

Les conversions de style cast et fonction ont les mêmes résultats en convertissant à partir de valeurs uniques. Toutefois, dans la syntaxe de style fonction, vous pouvez spécifier plusieurs arguments pour la conversion. Cette différence est importante pour les types définis par l'utilisateur. Prenons une classe `Point` et ses conversions :

```cpp
struct Point
{
    Point( short x, short y ) { _x = x; _y = y; }
    ...
    short _x, _y;
};
...
Point pt = Point( 3, 10 );
```

L’exemple précédent, qui utilise la conversion de style fonction, montre comment convertir deux valeurs (une pour *x* et une pour *y*) en un type défini par l’utilisateur `Point` .

> [!CAUTION]
> Utilisez les conversions de type explicites avec précaution, car elles remplacent la vérification de type intégrée du compilateur C++.

La notation de [Cast](../cpp/cast-operator-parens.md) doit être utilisée pour les conversions en types qui n’ont pas de *type simple-type-name* (pointeur ou types référence, par exemple). La conversion en types pouvant être exprimés à l’aide d’un *simple-type-name* peut être écrite sous l’une ou l’autre forme.

La définition de type avec des casts n'est pas conforme.

## <a name="see-also"></a>Voir aussi

[Expressions suffixées](../cpp/postfix-expressions.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
