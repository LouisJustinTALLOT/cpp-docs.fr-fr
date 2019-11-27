---
title: Tableaux (C++)
ms.date: 11/14/2019
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 91c57a9c4ef190dcace1813dd81739ac72e6b358
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188988"
---
# <a name="arrays-c"></a>Tableaux (C++)

Un tableau est une séquence d’objets du même type qui occupent une zone contiguë de mémoire. Les tableaux de style C traditionnels sont la source de nombreux bogues, mais restent communs, en particulier dans les bases de code plus anciennes. Dans moderne C++, nous vous recommandons fortement d’utiliser [std :: Vector](../standard-library/vector-class.md) ou [std :: Array](../standard-library/array-class-stl.md) au lieu des tableaux de style C décrits dans cette section. Ces deux types de bibliothèques standard stockent leurs éléments sous la forme d’un bloc de mémoire contigu, mais offrent une sécurité de type nettement supérieure avec les itérateurs qui pointent vers un emplacement valide dans la séquence. Pour plus d’informations, consultez [conteneurs ( C++moderne)](containers-modern-cpp.md).

## <a name="stack-declarations"></a>Déclarations de pile

Dans une C++ déclaration de tableau, la taille du tableau est spécifiée après le nom de la variable, et non après le nom de type, comme dans d’autres langages. L’exemple suivant déclare un tableau de 1000 doubles à allouer sur la pile. Le nombre d’éléments doit être fourni sous la forme d’un littéral entier ou d’une expression constante, car le compilateur doit connaître la quantité d’espace de pile à allouer. elle ne peut pas utiliser une valeur calculée au moment de l’exécution. La valeur par défaut 0 est affectée à chaque élément du tableau. Si vous n’affectez pas de valeur par défaut, chaque élément contient initialement les valeurs aléatoires qui se trouvent à cet emplacement.

```cpp
    constexpr size_t size = 1000;

    // Declare an array of doubles to be allocated on the stack
    double numbers[size] {0};

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i-1] * 1.1;
    }

    // Access each element
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }
```

Le premier élément du tableau est l’élément 0, et le dernier élément est l’élément (*n*-1), où *n* est le nombre d’éléments que le tableau peut contenir. Le nombre d’éléments dans la déclaration doit être de type intégral et doit être supérieur à 0. Il vous incombe de vous assurer que votre programme ne transmet jamais une valeur à l’opérateur d’indice supérieur à `(size - 1)`.

Un tableau de taille zéro est légal uniquement lorsque le tableau est le dernier champ d’un **struct** ou d’une **Union** et lorsque les extensions Microsoft (/Ze) sont activées.

Les tableaux basés sur la pile sont plus rapides à allouer et à utiliser que les tableaux basés sur les tas, mais le nombre d’éléments ne peut pas être tellement important qu’il utilise trop de mémoire de pile. Le niveau de dépendance dépend de votre programme. Vous pouvez utiliser les outils de profilage pour déterminer si un tableau est trop grand.

## <a name="heap-declarations"></a>Déclarations de tas

Si vous avez besoin d’un tableau qui est trop grand pour être alloué sur la pile, ou dont la taille ne peut pas être connue au moment de la compilation, vous pouvez l’allouer sur le tas avec une [nouvelle\[\]](new-operator-cpp.md) expression. L’opérateur retourne un pointeur vers le premier élément. Vous pouvez utiliser l’opérateur d’indice avec la variable de pointeur comme avec un tableau basé sur la pile. Vous pouvez également utiliser des [opérations arithmétiques sur les pointeurs](../c-language/pointer-arithmetic.md) pour déplacer le pointeur vers n’importe quel élément arbitraire dans le tableau. Il vous incombe de veiller à ce que :

- vous conservez toujours une copie de l’adresse du pointeur d’origine afin de pouvoir supprimer la mémoire lorsque vous n’avez plus besoin du tableau.
- vous ne pouvez pas incrémenter ou décrémenter l’adresse du pointeur au-delà des limites du tableau.

L’exemple suivant montre comment définir un tableau sur le tas au moment de l’exécution et comment accéder aux éléments du tableau à l’aide de l’opérateur d’indice ou de l’arithmétique du pointeur :

```cpp

void do_something(size_t size)
{
    // Declare an array of doubles to be allocated on the heap
    double* numbers = new double[size]{ 0 };

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i - 1] * 1.1;
    }

    // Access each element with subscript operator
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }

    // Access each element with pointer arithmetic
    // Use a copy of the pointer for iterating
    double* p = numbers;

    for (size_t i = 0; i < size; i++)
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    // Alternate method:
    // Reset p to numbers[0]:
    p = numbers;

    // Use address of pointer to compute bounds.
    // The compiler computes size as the number
    // of elements * (bytes per element).
    while (p < (numbers + size))
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    delete[] numbers; // don't forget to do this!

}
int main()
{
    do_something(108);
}

```

## <a name="initializing-arrays"></a>Initialisation des tableaux

Vous pouvez initialiser un tableau dans une boucle, un élément à la fois ou dans une instruction unique. Le contenu des deux tableaux suivants est identique :

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>Passage de tableaux à des fonctions

Lorsqu’un tableau est passé à une fonction, il est passé en tant que pointeur vers le premier élément. Cela est vrai pour les tableaux basés sur la pile et sur les tas. Le pointeur ne contient aucune information de taille ou de type supplémentaire. Ce comportement est appelé *atténuation du pointeur*. Quand vous transmettez un tableau à une fonction, vous devez toujours spécifier le nombre d’éléments dans un paramètre séparé. Ce comportement implique également que les éléments de tableau ne sont pas copiés lorsque le tableau est passé à une fonction. Pour empêcher la fonction de modifier les éléments, spécifiez le paramètre en tant que pointeur vers des éléments **const** .

L’exemple suivant montre une fonction qui accepte un tableau et une longueur. Le pointeur pointe vers le tableau d’origine, pas une copie. Étant donné que le paramètre n’est pas **const**, la fonction peut modifier les éléments du tableau.

```cpp
void process(double p*, const size_t len)
{
    std::cout << "process:\n";
    for (size_t i = 0; i < len; ++i)
    {
        // do something with p[i]
    }
}
```

Déclarez le tableau comme const pour le rendre accessible en lecture seule dans le bloc de fonction :

```cpp
void process(const double p*, const size_t len);
```

La même fonction peut également être déclarée de cette manière, sans modification du comportement. Le tableau est toujours passé comme pointeur vers le premier élément :

```cpp
// Unsized array
void process(const double p[] const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>Tableaux multidimensionnels

Les tableaux construits à partir d'autres tableaux sont des tableaux multidimensionnels. Ces tableaux multidimensionnels sont spécifiés en plaçant dans l'ordre plusieurs expressions de constantes entre accolades. Par exemple, observez cette déclaration :

```cpp
int i2[5][7];
```

Elle spécifie un tableau de type **int**, organisé de manière conceptuelle dans une matrice à deux dimensions de cinq lignes et sept colonnes, comme illustré dans la figure suivante :

![Disposition conceptuelle d’un tableau&#45;multidimensionnel](../cpp/media/vc38rc1.gif "Disposition conceptuelle d’un tableau&#45;multidimensionnel") <br/>
Disposition conceptuelle d'un tableau multidimensionnel

Dans les déclarations de tableaux multidimensionnels qui ont une liste d’initialiseurs (comme décrit dans [initialiseurs](../cpp/initializers.md)), l’expression constante qui spécifie les limites de la première dimension peut être omise. Exemple :

```cpp
// arrays2.cpp
// compile with: /c
const int cMarkets = 4;
// Declare a float that represents the transportation costs.
double TransportCosts[][cMarkets] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};
```

La déclaration précédente définit un tableau composé de trois lignes et de quatre colonnes. Les lignes représentent les fabriques et les colonnes les marchés auxquels les fabriques livrent. Les valeurs sont les coûts de transport entre les fabriques et les marchés. La première dimension du tableau est omise, mais le compilateur la complète en examinant l'initialiseur.

L’utilisation de l’opérateur d’indirection (*) sur un type de tableau multidimensionnel produit un tableau à n-1 dimensions. Si n correspond à 1, une variable scalaire (ou un élément de tableau) est générée.

Les tableaux C++ sont stockés dans l'ordre row-major. L'ordre row-major signifie que le dernier indice varie le plus rapidement.

## <a name="example"></a>Exemple

La technique d'omission des spécifications de limites de la première dimension d'un tableau multidimensionnel peut également être utilisée dans les déclarations de fonction comme suit :

```cpp
// multidimensional_arrays.cpp
// compile with: /EHsc
// arguments: 3
#include <limits>   // Includes DBL_MAX
#include <iostream>

const int cMkts = 4, cFacts = 2;

// Declare a float that represents the transportation costs
double TransportCosts[][cMkts] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};

// Calculate size of unspecified dimension
const int cFactories = sizeof TransportCosts /
                  sizeof( double[cMkts] );

double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);

using namespace std;

int main( int argc, char *argv[] ) {
   double MinCost;

   if (argv[1] == 0) {
      cout << "You must specify the number of markets." << endl;
      exit(0);
   }
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);
   cout << "The minimum cost to Market " << argv[1] << " is: "
       << MinCost << "\n";
}

double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {
   double MinCost = DBL_MAX;

   for( size_t i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

La fonction `FindMinToMkt` est écrite de telle sorte que l'ajout de nouvelles fabriques ne requiert aucune modification du code, juste une recompilation.

## <a name="initializing-arrays"></a>Initialisation des tableaux

Si une classe a un constructeur, les tableaux de cette classe sont initialisés par un constructeur. S'il y a moins d'éléments dans la liste d'initialiseurs que les éléments du tableau, le constructeur par défaut est utilisé pour les éléments restants. Si aucun constructeur par défaut n'est défini pour la classe, la liste d'initialiseurs doit être complète (autrement dit, il doit y avoir un initialiseur pour chaque élément du tableau.)

Prenons la classe `Point` qui définit deux constructeurs :

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

Le premier élément de `aPoint` est construit en utilisant le constructeur `Point( int, int )`. Les deux éléments restants sont construits à l'aide du constructeur par défaut.

Les tableaux membres statiques (qu’il s’agisse de **const** ou not) peuvent être initialisés dans leurs définitions (en dehors de la déclaration de classe). Exemple :

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```

## <a name="accessing-array-elements"></a>Accès aux éléments de tableau

Vous pouvez accéder à des éléments individuels d’un tableau à l’aide de l’opérateur d’indice de tableau (`[ ]`). Si un tableau unidimensionnel est utilisé dans une expression qui n’a pas d’indice, le nom du tableau prend la valeur d’un pointeur vers le premier élément du tableau.

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

Lorsque vous utilisez des tableaux multidimensionnels, vous pouvez utiliser différentes combinaisons dans les expressions.

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

Dans le code précédent, `multi` est un tableau à trois dimensions de type **double**. Le pointeur `p2multi` pointe vers un tableau de type **double** de la taille trois. Dans cet exemple, le tableau est utilisé avec un, deux et trois indices. Bien qu’il soit plus courant de spécifier tous les indices, comme dans l’instruction `cout`, il est parfois utile de sélectionner un sous-ensemble spécifique d’éléments de tableau, comme indiqué dans les instructions qui suivent `cout`.

## <a name="overloading-subscript-operator"></a>Surcharge de l’opérateur d’indice

Comme les autres opérateurs, l’opérateur d’indice (`[]`) peut être redéfini par l’utilisateur. Le comportement par défaut de l'opérateur d'indice, s'il n'est pas surchargé, est de combiner le nom d'un tableau et l'indice à l'aide de la méthode suivante :

`*((array_name) + (subscript))`

Comme dans toute addition qui implique des types pointeur, la mise à l'échelle est exécutée automatiquement pour ajuster la taille du type. Par conséquent, la valeur résultante n’est pas *n* octets de l’origine de Array-Name ; au lieu de cela, il s’agit du *n*ième élément du tableau. Pour plus d’informations sur cette conversion, consultez [opérateurs additifs](additive-operators-plus-and.md).

De même, pour des tableaux multidimensionnels, l'adresse est dérivée à l'aide de la méthode suivante :

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>Tableaux dans les expressions

Lorsqu’un identificateur d’un type tableau apparaît dans une expression autre que `sizeof`, adresse-de (`&`) ou initialisation d’une référence, il est converti en pointeur vers le premier élément du tableau. Exemple :

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

Le pointeur `psz` pointe vers le premier élément du tableau `szError1`. Contrairement aux pointeurs, les tableaux ne sont pas des l-value modifiables. Par conséquent, l'assignation suivante n'est pas conforme :

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Voir aussi

[std :: Array](../standard-library/array-class-stl.md)
