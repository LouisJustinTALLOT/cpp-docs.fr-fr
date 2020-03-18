---
title: '&lt;numeric&gt;, fonctions'
description: Décrit les modèles de fonction fournis par l’en-tête de&gt;C++ numérique &lt;dans la bibliothèque standard.
ms.date: 10/30/2019
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::exclusive_scan
- numeric/std::gcd
- numeric/std::inclusive_scan
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::lcm
- numeric/std::partial_sum
- numeric/std::reduce
- numeric/std::transform_exclusive_scan
- numeric/std::transform_inclusive_scan
- numeric/std::transform_reduce
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::exclusive_scan [C++]
- std::gcd [C++]
- std::inclusive_scan [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::lcm [C++]
- std::partial_sum [C++]
- std::reduce [C++]
- std::transform_exclusive_scan [C++]
- std::transform_inclusive_scan [C++]
- std::transform_reduce [C++]
ms.openlocfilehash: 88a97a3d110c684090b78570077927e32541eed7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419783"
---
# <a name="ltnumericgt-functions"></a>&lt;numeric&gt;, fonctions

## <a name="accumulate"></a>accumuler

Calcule la somme de tous les éléments d’une plage spécifiée, y compris une valeur initiale, en calculant des sommes partielles successives. Ou calcule le résultat des résultats partiels successifs d’une opération binaire spécifiée.

```cpp
template <class InputIterator, class Type>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée qui traite le premier élément de la plage à additionner ou à combiner à l’aide de *binary_op*.

*dernier*\
Itérateur d’entrée qui traite le dernier élément de la plage pour additionner ou combiner à l’aide de *binary_op*, il s’agit d’une position au-delà de l’élément final réellement inclus dans l’accumulation itérée.

\ *init*
Valeur initiale à laquelle chaque élément est ajouté à son tour ou combiné à l’aide de *binary_op*.

*binary_op*\
Opération binaire à appliquer à chaque élément de la plage spécifiée et au résultat de ses applications précédentes.

### <a name="return-value"></a>Valeur retournée

La somme de *init* et de tous les éléments de la plage spécifiée pour la première fonction de modèle, ou pour la deuxième fonction de modèle, le résultat de l’application de l’opération binaire *binary_op* au lieu de l’opération Sum, à (* PartialResult, *in_iter*), où *PartialResult* est le résultat des applications précédentes de l’opération et *in_iter* est un itérateur pointant vers l’élément suivant de la plage.

### <a name="remarks"></a>Notes

La valeur initiale garantit qu’il y a un résultat bien défini quand la plage est vide, auquel cas *init* est retourné. Il n’est pas nécessaire que l’opération binaire soit associative ou commutative. Le résultat est initialisé à la valeur initiale *init* , puis *result* = *binary_op*(*result*, *in_iter*) est calculé de façon itérative dans la plage, où *in_iter* est un itérateur pointant vers chaque élément successif de la plage. La plage doit être valide et la complexité est linéaire avec la taille de la plage. Le type de retour de l’opérateur binaire doit être convertible en **Type** pour assurer la fermeture pendant l’itération.

### <a name="example"></a>Exemple

```cpp
// numeric_accum.cpp
// compile with: /EHsc
#include <vector>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2(20);
   vector <int>::iterator iter1, iter2;

   int i;
   for (i = 1; i < 21; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   // The first member function for the accumulated sum
   int total;
   total = accumulate(v1.begin(), v1.end(), 0);

   cout << "The sum of the integers from 1 to 20 is: "
        << total << "." << endl;

   // Constructing a vector of partial sums
   int j = 0, partotal;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      partotal = accumulate(v1.begin(), iter1 + 1, 0);
      v2[j] = partotal;
      j++;
   }

   cout << "The vector of partial sums is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function for the accumulated product
   vector <int> v3, v4(10);
   vector <int>::iterator iter3, iter4;

   int s;
   for (s = 1; s < 11; s++)
   {
      v3.push_back(s);
   }

   cout << "The original vector v3 is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl;

   int ptotal;
   ptotal = accumulate(v3.begin(), v3.end(), 1, multiplies<int>());

   cout << "The product of the integers from 1 to 10 is: "
        << ptotal << "." << endl;

   // Constructing a vector of partial products
   int k = 0, ppartotal;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++) {
      ppartotal = accumulate(v3.begin(), iter3 + 1, 1, multiplies<int>());
      v4[k] = ppartotal;
      k++;
   }

   cout << "The vector of partial products is:\n ( " ;
   for (iter4 = v4.begin(); iter4 != v4.end(); iter4++)
      cout << *iter4 << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The sum of the integers from 1 to 20 is: 210.
The vector of partial sums is:
( 1 3 6 10 15 21 28 36 45 55 66 78 91 105 120 136 153 171 190 210 ).

The original vector v3 is:
( 1 2 3 4 5 6 7 8 9 10 ).
The product of the integers from 1 to 10 is: 3628800.
The vector of partial products is:
( 1 2 6 24 120 720 5040 40320 362880 3628800 ).
```

## <a name="adjacent_difference"></a>adjacent_difference

Calcule les différences successives entre chaque élément et son prédécesseur dans une plage d’entrée. Génère les résultats dans une plage de destination. Ou calcule le résultat d’une procédure généralisée dans laquelle l’opération de différence est remplacée par une autre opération binaire spécifiée.

```cpp
template <class InputIterator, class OutIterator>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIterator, class BinaryOperation>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Paramètres

\ d' *exécution*
Stratégie d’exécution.

*premier*\
Itérateur d'entrée qui traite le premier élément d'une plage d'entrée dont les éléments doivent être différenciés de leurs prédécesseurs respectifs, ou bien, dont la paire de valeurs doit être utilisée dans le cadre d'une opération par une opération binaire spécifiée.

*dernier*\
Itérateur d'entrée qui traite le dernier élément d'une plage d'entrée dont les éléments doivent être différenciés de leurs prédécesseurs respectifs, ou bien, dont la paire de valeurs doit être utilisée dans le cadre d'une opération par une opération binaire spécifiée.

\ de *résultats*
Itérateur de sortie qui traite le premier élément d'une plage de destination dans laquelle les différences ou les résultats de l'opération spécifiée doivent être enregistrés.

*binary_op*\
Opération binaire à appliquer dans l’opération généralisée, en remplaçant l’opération de soustraction dans la procédure de différenciation.

### <a name="return-value"></a>Valeur retournée

Itérateur de sortie ciblant la fin de la plage de destination : `result` + (`last` - `first`).

### <a name="remarks"></a>Notes

Le *résultat* de l’itérateur de sortie peut être le même que l’itérateur d’entrée en *premier*, afin que les valeurs `adjacent_difference` puissent être calculées sur place.

Pour une séquence *de valeurs 1, a 2* *,* *a*3, dans une plage d’entrée, la première fonction de modèle stocke les valeurs de `adjacent_difference` successives 1, *a*2- *a*1, a3- *a*2, dans la *plage de destination*.

Pour une séquence *de valeurs 1, a 2* *,* *a*3, dans une plage d’entrée, la deuxième fonction de modèle stocke les valeurs *de*`adjacent_difference` successives 1, *a*2 *binary_op* *1,* *a*3 *binary_op* *a*2, dans la plage de destination.

L’opération binaire *binary_op* ne doit pas être associative ou commutative, car l’ordre des opérations appliquées est spécifié.

### <a name="example"></a>Exemple

```cpp
// numeric_adj_diff.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend, LIterend2;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t * t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the adjacent_differences of
   // elements in a list output to a vector
   VIterend = adjacent_difference ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "Output vector containing adjacent_differences is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the adjacent products of the elements in a list
   VIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the adjacent products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of adjacent_differences in place
   LIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "In place output adjacent_differences in list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend2 ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="exclusive_scan"></a>exclusive_scan

Calcule une opération de somme de préfixe exclusive à l’aide d' `std::plus<>()` ou d’un opérateur binaire spécifié sur une plage, en fonction d’une valeur initiale. Écrit les résultats dans la plage en commençant à la destination spécifiée. Une somme de *préfixe exclusive* signifie que le *n*ième élément d’entrée n’est pas inclus dans la *n*ième somme. Les surcharges qui incluent un argument de stratégie d’exécution s’exécutent conformément à la stratégie spécifiée.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init);

template<class InputIterator, class OutputIterator, class Type, class BinaryOperation>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Paramètres

\ d' *exécution*
Stratégie d’exécution.

*premier*\
Itérateur d’entrée qui traite le premier élément de la plage à additionner ou à combiner à l’aide de *binary_op*.

*dernier*\
Itérateur d’entrée qui traite le dernier élément de la plage pour additionner ou combiner à l’aide de *binary_op*, il s’agit d’une position au-delà de l’élément final réellement inclus dans l’accumulation itérée.

\ de *résultats*
Itérateur de sortie qui traite le premier élément d’une plage de destination où les séries de sommes ou les résultats de l’opération spécifiée doivent être stockés.

\ *init*
Valeur initiale à laquelle chaque élément est ajouté à son tour ou combiné à l’aide de *binary_op*.

*binary_op*\
Opération binaire à appliquer à chaque élément de la plage spécifiée et au résultat de ses applications précédentes.

### <a name="return-value"></a>Valeur retournée

Itérateur de sortie ciblant la fin de la plage de destination : *résultat* + (*dernier* - en *premier*).

## <a name="gcd"></a>GCD

Calcule le plus grand commun diviseur des entiers m et n.

```cpp
template <class M, class N>
constexpr common_type_t<M,N> gcd(M m, N n);
```

### <a name="parameters"></a>Paramètres

*m*, *n*\
Valeurs de type intégral.

### <a name="return-value"></a>Valeur retournée

Retourne le plus grand commun dénominateur des valeurs absolues de *m* et *n*, ou zéro si *m* et *n* sont nuls. Les résultats sont indéfinis si les valeurs absolues de *m* ou *n* ne peuvent pas être représentées en tant que valeurs de type `common_type_t<M,N>`.

## <a name="inclusive_scan"></a>inclusive_scan

Calcule une opération de somme de préfixe inclusive à l’aide d' `std::plus<>()` ou d’un opérateur binaire spécifié sur une plage, en fonction d’une valeur initiale. Écrit les résultats dans la plage en commençant à la destination spécifiée. Une somme de *préfixes inclusive* signifie que le *n*ième élément d’entrée est inclus dans la *n*ième somme. Les surcharges qui incluent un argument de stratégie d’exécution s’exécutent conformément à la stratégie spécifiée.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template<class InputIterator, class OutputIterator, class BinaryOperation>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class Type>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation, class Type>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    Type init);
```

### <a name="parameters"></a>Paramètres

\ d' *exécution*
Stratégie d’exécution.

*premier*\
Itérateur d’entrée qui traite le premier élément de la plage à additionner ou à combiner à l’aide de *binary_op*.

*dernier*\
Itérateur d’entrée qui traite le dernier élément de la plage pour additionner ou combiner à l’aide de *binary_op*, il s’agit d’une position au-delà de l’élément final réellement inclus dans l’accumulation itérée.

\ de *résultats*
Itérateur de sortie qui traite le premier élément d’une plage de destination où les séries de sommes ou les résultats de l’opération spécifiée doivent être stockés.

\ *init*
Valeur initiale à laquelle chaque élément est ajouté à son tour ou combiné à l’aide de *binary_op*.

*binary_op*\
Opération binaire à appliquer à chaque élément de la plage spécifiée et au résultat de ses applications précédentes.

### <a name="return-value"></a>Valeur retournée

Itérateur de sortie ciblant la fin de la plage de destination : *résultat* + (*dernier* - en *premier*).

## <a name="inner_product"></a>inner_product

Calcule la somme du produit d’éléments de deux plages et l’ajoute à une valeur initiale spécifiée, ou calcule le résultat d’une procédure généralisée dans laquelle les opérations binaires de somme et de produit sont remplacées par d’autres opérations binaires spécifiées.

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);
```

### <a name="parameters"></a>Paramètres

*first1*\
Itérateur d’entrée qui traite le premier élément de la première plage dont le produit interne ou le produit interne généralisé avec la deuxième plage est à calculer.

*last1*\
Itérateur d’entrée qui traite le dernier élément de la première plage dont le produit interne ou le produit interne généralisé avec la deuxième plage est à calculer.

*first2*\
Itérateur d’entrée qui traite le premier élément de la deuxième plage dont le produit interne ou le produit interne généralisé avec la première plage est à calculer.

\ *init*
Valeur initiale à laquelle ajouter le produit interne ou le produit interne généralisé entre les plages.

*binary_op1*\
Opération binaire qui remplace l’opération de somme du produit interne appliquée aux produits d’éléments dans la généralisation du produit interne.

*binary_op2*\
Opération binaire qui remplace l’opération de multiplication des éléments du produit interne dans la généralisation du produit interne.

### <a name="return-value"></a>Valeur retournée

La première fonction membre retourne la somme des produits d’éléments et y ajoute la valeur initiale spécifiée. Pour les plages de valeurs *a*i et *b*i, elle retourne :

*init* + (*a*1 \* *b*1) + (*a*2 \* *b*2) +... + (*a*n \* *b*n)

en remplaçant de manière itérative *init* par *init* + (*a*i \* *b*i).

La deuxième fonction membre retourne :

*init* *binary_op1* (*a*1 *binary_op2* *b*1) *binary_op1* (*a*2 *binary_op2* *b*2) *binary_op1* ... *binary_op1* (*a*n *binary_op2* *b*n)

en remplaçant de manière itérative *init* par *init* *binary_op1* (*a*i *binary_op2* *b*i).

### <a name="remarks"></a>Notes

La valeur initiale garantit qu’il y a un résultat bien défini quand la plage est vide. Dans ce cas, *init* est retourné. Les opérations binaires n’ont pas besoin d’être associatives ou commutates. La plage doit être valide et la complexité est linéaire avec la taille de la plage. Le type de retour de l’opérateur binaire doit être convertible en **Type** pour assurer la fermeture pendant l’itération.

### <a name="example"></a>Exemple

```cpp
// numeric_inner_prod.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   vector <int> v1, v2(7), v3(7);
   vector <int>::iterator iter1, iter2, iter3;

   int i;
   for (i = 1; i <= 7; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   list <int> l1, l2(7);
   list <int>::iterator lIter1, lIter2;

   int t;
   for (t = 1; t <= 7; t++)
   {
      l1.push_back(t);
   }

   cout << "The original list l1 is:\n ( " ;
   for (lIter1 = l1.begin(); lIter1 != l1.end(); lIter1++)
      cout << *lIter1 << " ";
   cout << ")." << endl;

   // The first member function for the inner product
   int inprod;
   inprod = inner_product(v1.begin(), v1.end(), l1.begin(), 0);

   cout << "The inner_product of the vector v1 and the list l1 is: "
        << inprod << "." << endl;

   // Constructing a vector of partial inner_products between v1 & l1
   int j = 0, parinprod;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++) {
      parinprod = inner_product(v1.begin(), iter1 + 1, l1.begin(), 0);
      v2[j] = parinprod;
      j++;
   }

   cout << "Vector of partial inner_products between v1 & l1 is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function used to compute
   // the product of the element-wise sums
   int inprod2;
   inprod2 = inner_product (v1.begin(), v1.end(),
      l1.begin(), 1, multiplies<int>(), plus<int>());

   cout << "The sum of the element-wise products of v1 and l1 is: "
        << inprod2 << "." << endl;

   // Constructing a vector of partial sums of element-wise products
   int k = 0, parinprod2;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      parinprod2 =
         inner_product(v1.begin(), iter1 + 1, l1.begin(), 1,
         multiplies<int>(), plus<int>());
      v3[k] = parinprod2;
      k++;
   }

   cout << "Vector of partial sums of element-wise products is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl << endl;
}
```

## <a name="iota"></a>culbut

Stocke une valeur de départ, en commençant par le premier élément et en remplissant les incréments successifs de cette valeur (`value++`) dans chacun des éléments de l’intervalle `[first,  last)`.

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée qui traite le premier élément de la plage à remplir.

*dernier*\
Itérateur d’entrée qui traite le dernier élément de la plage à remplir.

*value*\
Valeur de départ à stocker dans le premier élément et à incrémenter successivement les éléments ultérieurs.

### <a name="example"></a>Exemple

L’exemple suivant montre certaines utilisations de la fonction `iota` en remplissant une liste d’entiers ([list](../standard-library/list.md)), puis en remplissant un vecteur ([vector](../standard-library/vector.md)) avec les valeurs `list` pour pouvoir utiliser la fonction [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle).

```cpp
// compile by using: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <numeric>
#include <list>
#include <vector>
#include <iostream>

using namespace std;

int main(void)
{
    list <int> intList(10);
    vector <list<int>::iterator> intVec(intList.size());

    // Fill the list
    iota(intList.begin(), intList.end(), 0);

    // Fill the vector with the list so we can shuffle it
    iota(intVec.begin(), intVec.end(), intList.begin());

    random_shuffle(intVec.begin(), intVec.end());

    // Output results
    cout << "Contents of the integer list: " << endl;
    for (auto i: intList) {
        cout << i << ' ';
    }
    cout << endl << endl;

    cout << "Contents of the integer list, shuffled by using a vector: " << endl;
    for (auto i: intVec) {
        cout << *i << ' ';
    }
    cout << endl;
}
```

## <a name="lcm"></a>LCM

```cpp
template <class M, class N>
constexpr common_type_t<M,N> lcm(M m, N n);
```

## <a name="partial_sum"></a>partial_sum

Calcule une série de sommes dans une plage d’entrée à partir du premier élément dans le *n*ième élément et stocke le résultat de chaque somme dans le *n*ième élément d’une plage de destination. Ou calcule le résultat d’une procédure généralisée où l’opération Sum est remplacée par une autre opération binaire spécifiée.

```cpp
template <class InputIterator, class OutIt>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIt, class Fn2>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d'entrée qui traite le premier élément de la plage qui doit être partiellement additionné ou combiné, selon l'opération binaire spécifiée.

*dernier*\
Itérateur d'entrée qui traite le dernier élément d'une plage qui doit être partiellement additionné ou combiné selon une opération binaire spécifiée, et dont la position se trouve immédiatement après le dernier élément inclus dans l'accumulation itérée.

\ de *résultats*
Itérateur de sortie qui traite le premier élément d’une plage de destination pour stocker la série de sommes partielles ou les résultats successifs de l’opération binaire spécifiée.

*binary_op*\
Opération binaire à appliquer dans l’opération généralisée, en remplaçant l’opération de Sum dans la procédure de somme partielle.

### <a name="return-value"></a>Valeur retournée

Itérateur de sortie ciblant la fin de la plage de destination : *résultat* + (*dernier* - en *premier*).

### <a name="remarks"></a>Notes

Le *résultat* de l’itérateur de sortie peut être le même que l’itérateur d’entrée en *premier*, afin que les sommes partielles puissent être calculées sur place.

Pour *une séquence de valeurs 1*, *a*2,... *un*x, dans une plage d’entrée, la première fonction de modèle stocke des sommes partielles successives dans la plage de destination. Le *n*ième élément est fourni par (*a*1 + *a*2 + *a*3 +... + *a*n).

Pour une séquence *de valeurs 1, a 2* *,* *a*3, dans une plage d’entrée, la deuxième fonction de modèle stocke des résultats partiels successifs dans la plage de destination. Le *n*ième élément est fourni par ((... *((1* *binary_op* *2)* *binary_op* *a*3) *binary_op* ...) *binary_op* *un*n).

L’opération binaire *binary_op* ne doit pas être associative ou commutative, car l’ordre des opérations appliquées est spécifié.

### <a name="example"></a>Exemple

```cpp
// numeric_partial_sum.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the partial sums of
   // elements in a list output to a vector
   VIterend = partial_sum ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "The output vector containing the partial sums is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the partial product of the elements in a list
   VIterend2 = partial_sum ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the partial products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of partial sums in place
   LIterend = partial_sum ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "The in place output partial_sum list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="reduce"></a>abaisse

Réduit tous les éléments d’une plage spécifiée, y compris éventuellement une valeur initiale, en calculant des sommes dans un ordre arbitraire et éventuellement permuté. Ou réduit en calculant les résultats d’une opération binaire spécifiée. Les surcharges qui incluent un argument de stratégie d’exécution s’exécutent conformément à la stratégie spécifiée.

```cpp
template<class InputIterator>
typename iterator_traits<InputIterator>::value_type reduce(
    InputIterator first,
    InputIterator last);

template<class InputIterator, class Type>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init);

template<class InputIterator, class Type, class BinaryOperation>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator>
typename iterator_traits<ForwardIterator>::value_type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Type>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Paramètres

\ d' *exécution*
Stratégie d’exécution.

*premier*\
Itérateur d’entrée qui traite le premier élément de la plage à additionner ou à combiner à l’aide de *binary_op*.

*dernier*\
Itérateur d’entrée qui traite le dernier élément de la plage pour additionner ou combiner à l’aide de *binary_op*, il s’agit d’une position au-delà de l’élément final réellement inclus dans l’accumulation itérée.

\ de *résultats*
Itérateur de sortie qui traite le premier élément d’une plage de destination où les séries de sommes ou les résultats de l’opération spécifiée doivent être stockés.

\ *init*
Valeur initiale à laquelle chaque élément est ajouté à son tour ou combiné à l’aide de *binary_op*.

*binary_op*\
Opération binaire à appliquer à chaque élément de la plage spécifiée et au résultat de ses applications précédentes.

### <a name="return-value"></a>Valeur retournée

Résultat de l’application de *binary_op* ou `std::plus<>()` *à init* et de tous les éléments de la plage spécifiée à (* PartialResult, *in_iter*), où *PartialResult* est le résultat des applications précédentes de l’opération, et *in_iter* est un itérateur pointant vers un élément de la plage. Dans les surcharges qui ne spécifient pas *init*, la valeur *init* utilisée équivaut à `typename iterator_traits<InputIterator>::value_type{}`.

### <a name="remarks"></a>Notes

`reduce` comportement n’est pas déterministe, à moins que *binary_op* soit associatif et mutative. Le comportement n’est pas défini si *binary_op* modifie un élément, ou invalide tout itérateur dans l’intervalle \[*premier*, *dernier*], inclus.

## <a name="transform_exclusive_scan"></a>transform_exclusive_scan

Transforme les éléments d’une plage avec un opérateur unaire spécifié, puis calcule une opération de somme de préfixe exclusive à l’aide d' `std::plus<>()` ou d’un opérateur binaire spécifié sur la plage, en fonction d’une valeur initiale. Écrit les résultats dans la plage en commençant à la destination spécifiée. Une somme de *préfixe exclusive* signifie que le *n*ième élément d’entrée n’est pas inclus dans la *n*ième somme. Les surcharges qui incluent un argument de stratégie d’exécution s’exécutent conformément à la stratégie spécifiée. La somme peut être effectuée dans un ordre arbitraire.

```cpp
template<class InputIterator, class OutputIterator, class Type, class BinaryOperation, class UnaryOperation>
OutputIterator transform_exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>Paramètres

\ d' *exécution*
Stratégie d’exécution.

*premier*\
Itérateur d’entrée qui traite le premier élément de la plage à additionner ou à combiner à l’aide de *binary_op*.

*dernier*\
Itérateur d’entrée qui traite le dernier élément de la plage pour additionner ou combiner à l’aide de *binary_op*, il s’agit d’une position au-delà de l’élément final réellement inclus dans l’accumulation itérée.

\ de *résultats*
Itérateur de sortie qui traite le premier élément d’une plage de destination où les séries de sommes ou les résultats de l’opération spécifiée doivent être stockés.

\ *init*
Valeur initiale à laquelle chaque élément est ajouté à son tour ou combiné à l’aide de *binary_op*.

*binary_op*\
Opération binaire à appliquer à chaque élément de la plage spécifiée et au résultat de ses applications précédentes.

*unary_op*\
Opération unaire à appliquer à chaque élément de la plage spécifiée.

## <a name="transform_inclusive_scan"></a>transform_inclusive_scan

Transforme les éléments d’une plage avec un opérateur unaire spécifié, puis calcule une opération de somme de préfixe inclusive à l’aide d' `std::plus<>()` ou d’un opérateur binaire spécifié sur la plage, en fonction d’une valeur initiale. Écrit les résultats dans la plage en commençant à la destination spécifiée. Une somme de *préfixes inclusive* signifie que le *n*ième élément d’entrée est inclus dans la *n*ième somme. Les surcharges qui incluent un argument de stratégie d’exécution s’exécutent conformément à la stratégie spécifiée. La somme peut être effectuée dans un ordre arbitraire.

```cpp
template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation, class Type>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation, class Type>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);
```

### <a name="parameters"></a>Paramètres

\ d' *exécution*
Stratégie d’exécution.

*premier*\
Itérateur d’entrée qui traite le premier élément de la plage à additionner ou à combiner à l’aide de *binary_op*.

*dernier*\
Itérateur d’entrée qui traite le dernier élément de la plage pour additionner ou combiner à l’aide de *binary_op*, il s’agit d’une position au-delà de l’élément final réellement inclus dans l’accumulation itérée.

\ de *résultats*
Itérateur de sortie qui traite le premier élément d’une plage de destination où les séries de sommes ou les résultats de l’opération spécifiée doivent être stockés.

*binary_op*\
Opération binaire à appliquer à chaque élément de la plage spécifiée et au résultat de ses applications précédentes.

*unary_op*\
Opération unaire à appliquer à chaque élément de la plage spécifiée.

\ *init*
Valeur initiale à laquelle chaque élément est ajouté à son tour ou combiné à l’aide de *binary_op*.

## <a name="transform_reduce"></a>transform_reduce

Transforme une plage d’éléments, puis applique un functor qui réduit les éléments transformés dans l’ordre arbitraire. En effet, une `transform` suivie d’une `reduce`.

```cpp
template<class InputIterator1, class InputIterator2, class Type>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init);

template<class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class InputIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>Paramètres

\ d' *exécution*
Stratégie d’exécution.

*premier*\
Itérateur d’entrée qui traite le premier élément de la plage à additionner ou à combiner à l’aide de *binary_op*.

*first1*\
Itérateur d’entrée qui traite le premier élément de la plage à additionner ou à combiner à l’aide de *binary_op1*.

*dernier*\
Itérateur d’entrée qui traite le dernier élément de la plage pour additionner ou combiner à l’aide de *binary_op*, il s’agit d’une position au-delà de l’élément final réellement inclus dans l’accumulation itérée.

*last1*\
Itérateur d’entrée qui traite le dernier élément de la plage pour additionner ou combiner à l’aide de *binary_op1*, il s’agit d’une position au-delà de l’élément final réellement inclus dans l’accumulation itérée.

\ de *résultats*
Itérateur de sortie qui traite le premier élément d’une plage de destination où les séries de sommes ou les résultats de l’opération spécifiée doivent être stockés.

\ *init*
Valeur initiale à laquelle chaque élément est ajouté à son tour ou combiné à l’aide de *binary_op*.

*binary_op*\
Opération binaire à appliquer à chaque élément de la plage spécifiée et au résultat de ses applications précédentes.

*unary_op*\
Opération unaire à appliquer à chaque élément de la plage spécifiée.

### <a name="return-value"></a>Valeur retournée

Résultat réduit, puis réduit.
