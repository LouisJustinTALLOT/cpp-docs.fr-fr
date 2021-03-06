---
description: 'En savoir plus sur : surcharge des opérateurs d’incrémentation et de décrémentation (C++)'
title: Surcharge d'opérateurs d'incrémentation et de décrémentation (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: f2704a1c10375bf8422324d90f41c6e3ac245505
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113920"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>Surcharge d'opérateurs d'incrémentation et de décrémentation (C++)

Les opérateurs d'incrémentation et de décrémentation appartiennent à une catégorie spéciale car chacun comporte deux variantes :

- Incrémentation préfixée et incrémentation suffixée

- Décrémentation préfixée et décrémentation suffixée

Lorsque vous écrivez des fonctions d'opérateur surchargées, il peut être utile d'implémenter des versions distinctes des versions préfixées et suffixées de ces opérateurs. Pour faire la distinction entre les deux, la règle suivante est observée : la forme de préfixe de l’opérateur est déclarée exactement de la même façon que tout autre opérateur unaire. le formulaire postfix accepte un argument supplémentaire de type **`int`** .

> [!NOTE]
> Quand vous spécifiez un opérateur surchargé pour la forme suffixée de l’opérateur d’incrémentation ou de décrémentation, l’argument supplémentaire doit être de type **`int`** ; la spécification de tout autre type génère une erreur.

L'exemple suivant indique comment définir les opérateurs d'incrémentation et de décrémentation préfixés et suffixés pour la classe `Point` :

```cpp
// increment_and_decrement1.cpp
class Point
{
public:
   // Declare prefix and postfix increment operators.
   Point& operator++();       // Prefix increment operator.
   Point operator++(int);     // Postfix increment operator.

   // Declare prefix and postfix decrement operators.
   Point& operator--();       // Prefix decrement operator.
   Point operator--(int);     // Postfix decrement operator.

   // Define default constructor.
   Point() { _x = _y = 0; }

   // Define accessor functions.
   int x() { return _x; }
   int y() { return _y; }
private:
   int _x, _y;
};

// Define prefix increment operator.
Point& Point::operator++()
{
   _x++;
   _y++;
   return *this;
}

// Define postfix increment operator.
Point Point::operator++(int)
{
   Point temp = *this;
   ++*this;
   return temp;
}

// Define prefix decrement operator.
Point& Point::operator--()
{
   _x--;
   _y--;
   return *this;
}

// Define postfix decrement operator.
Point Point::operator--(int)
{
   Point temp = *this;
   --*this;
   return temp;
}
int main()
{
}
```

Les mêmes opérateurs peuvent être définis dans la portée de fichier (globalement) à l'aide des en-têtes de fonction suivants :

```cpp
friend Point& operator++( Point& )      // Prefix increment
friend Point& operator++( Point&, int ) // Postfix increment
friend Point& operator--( Point& )      // Prefix decrement
friend Point& operator--( Point&, int ) // Postfix decrement
```

L’argument de type **`int`** qui désigne la forme suffixée de l’opérateur d’incrémentation ou de décrémentation n’est pas couramment utilisé pour passer des arguments. Il contient généralement la valeur 0. Toutefois, il peut être utilisé comme suit :

```cpp
// increment_and_decrement2.cpp
class Int
{
public:
    Int &operator++( int n );
private:
    int _i;
};

Int& Int::operator++( int n )
{
    if( n != 0 )    // Handle case where an argument is passed.
        _i += n;
    else
        _i++;       // Handle case where no argument is passed.
    return *this;
}
int main()
{
   Int i;
   i.operator++( 25 ); // Increment by 25.
}
```

Il n'existe aucune autre syntaxe pour utiliser les opérateurs d'incrémentation ou de décrémentation pour passer ces valeurs que l'appel explicite, comme indiqué dans le code précédent. Une méthode plus simple pour implémenter cette fonctionnalité consiste à surcharger l’opérateur d’addition/assignation ( **+=** ).

## <a name="see-also"></a>Voir aussi

[Surcharge d’opérateur](../cpp/operator-overloading.md)
