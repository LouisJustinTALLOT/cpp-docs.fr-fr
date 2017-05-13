---
title: '&lt;numeric&gt;, fonctions | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::partial_sum
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
caps.latest.revision: 13
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: d194bebeb13d9a5e4648a7c74192047fe093576d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/19/2017

---
# <a name="ltnumericgt-functions"></a>&lt;numeric&gt;, fonctions
||||  
|-|-|-|  
|[accumulate](#accumulate)|[adjacent_difference](#adjacent_difference)|[inner_product](#inner_product)|  
|[iota](#iota)|[partial_sum](#partial_sum)|  
  
##  <a name="accumulate"></a>  accumulate  
 Calcule la somme de tous les éléments d’une plage spécifiée incluant une valeur initiale en calculant des sommes partielles successives, ou calcule le résultat des résultats partiels successifs obtenus de la même façon en utilisant une opération binaire spécifiée autre que la somme.  
  
```  
template <class InputIterator, class Type>  
Type accumulate(InputIterator first, InputIterator last, Type val);

template <class InputIterator, class Type, class BinaryOperation>  
Type accumulate(
    InputIterator first, 
    InputIterator last, 
    Type val, 
    BinaryOperation binary_op);
```  
  
### <a name="parameters"></a>Paramètres   
 `first`  
 Itérateur d’entrée qui traite le premier élément de la plage qui doit être additionné ou combiné, selon l’opération binaire spécifiée.  
  
 `last`  
 Itérateur d’entrée qui traite le dernier élément d’une plage qui doit être additionné ou combiné selon une opération binaire spécifiée et dont la position se trouve immédiatement après le dernier élément inclus dans l’accumulation itérée.  
  
 `val`  
 Valeur initiale à laquelle chaque élément est à son tour ajouté ou combiné selon une opération binaire spécifiée.  
  
 `binary_op`  
 Opération binaire qui doit être appliquée à chaque élément dans la plage spécifiée et le résultat de ses applications précédentes.  
  
### <a name="return-value"></a>Valeur de retour  
 Somme de `val` et de tous les éléments de la plage spécifiée pour la première fonction de modèle ou, pour la deuxième fonction de modèle, résultat de l’application de l’opération binaire spécifiée, au lieu de l’opération de somme, à ( *PartialResult, \*Iter*), où *PartialResult* est le résultat des applications précédentes de l’opération et `Iter` est un itérateur pointant vers un élément de la plage.  
  
### <a name="remarks"></a>Notes  
 La valeur initiale garantit l’obtention d’un résultat bien défini quand la plage est vide, auquel cas `val` est retourné. L’opération binaire n’est pas tenue d’être associative ou commutative. Le résultat est initialisé à la valeur initiale `val`, puis *result* = `binary_op` ( *result*, **\***`Iter`) est calculé de manière itérative dans la plage, où `Iter` est un itérateur qui pointe vers l’élément suivant dans la plage. La plage doit être valide et la complexité est linéaire par rapport à la taille de la plage. Le type de retour de l’opérateur binaire doit être convertible en **Type** pour assurer la fermeture pendant l’itération.  
  
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
  
##  <a name="adjacent_difference"></a>  adjacent_difference  
 Détermine les différences successives entre chaque élément et son prédécesseur au sein d'une plage d'entrée, puis génère les résultats dans une plage de destination ou calcule le résultat d'une procédure généralisée dans laquelle l'opération de différence est remplacée par une autre opération binaire spécifiée.  
  
```  
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
```  
  
### <a name="parameters"></a>Paramètres  
 `first`  
 Itérateur d'entrée qui traite le premier élément d'une plage d'entrée dont les éléments doivent être différenciés de leurs prédécesseurs respectifs, ou bien, dont la paire de valeurs doit être utilisée dans le cadre d'une opération par une opération binaire spécifiée.  
  
 `last`  
 Itérateur d'entrée qui traite le dernier élément d'une plage d'entrée dont les éléments doivent être différenciés de leurs prédécesseurs respectifs, ou bien, dont la paire de valeurs doit être utilisée dans le cadre d'une opération par une opération binaire spécifiée.  
  
 `result`  
 Itérateur de sortie qui traite le premier élément d'une plage de destination dans laquelle les différences ou les résultats de l'opération spécifiée doivent être enregistrés.  
  
 `binary_op`  
 Opération binaire qui doit être appliquée dans l'opération généralisée par le remplacement de l'opération de soustraction de la procédure de différenciation.  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur de sortie qui traite la fin de la plage de destination : `result` + ( `last` - `first`).  
  
### <a name="remarks"></a>Remarques  
 La _ d’itérateur de sortie *résultat* ne peut être le même que l’itérateur d’entrée * tout d’abord, * afin que `adjacent_difference`s peuvent être calculées sur place.  
  
 Pour une séquence de valeurs *un*1, *un*2, *un*3, dans une plage d’entrée, la première fonction de modèle stocke une successives **partial_difference**s *un*1, *un*2 - *un*1, a3 - *un*2, dans la plage de destination.  
  
 Pour une séquence de valeurs *a*1, *a*2, *a*3 dans une plage d’entrée, la deuxième fonction de modèle stocke les valeurs successives **partial_difference** *a*1, *a*2 `binary_op` *a*1, *a*3 `binary_op` *a*2 dans la plage de destination.  
  
 Il n'est pas nécessaire que l'opération binaire `binary_op` soit associative ou commutative, car l'ordre des opérations appliqué est entièrement spécifié.  
  
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
  
##  <a name="inner_product"></a>  inner_product  
 Calcule la somme du produit d’éléments de deux plages et l’ajoute à une valeur initiale spécifiée, ou calcule le résultat d’une procédure généralisée dans laquelle les opérations binaires de somme et de produit sont remplacées par d’autres opérations binaires spécifiées.  
  
```  
template <class InputIterator1, class InputIterator2, class Type>  
Type inner_product(
    InputIterator1   first1, 
    InputIterator1   last1, 
    InputIterator2   first2, 
    Type             val);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>  
Type inner_product(
    InputIterator1   first1, 
    InputIterator1   last1, 
    InputIterator2   first2, 
    Type             val, 
    BinaryOperation1  binary_op1, 
    BinaryOperation2  binary_op2);
```  
  
### <a name="parameters"></a>Paramètres  
 `first1`  
 Itérateur d’entrée qui traite le premier élément de la première plage dont le produit interne ou le produit interne généralisé avec la deuxième plage est à calculer.  
  
 `last1`  
 Itérateur d’entrée qui traite le dernier élément de la première plage dont le produit interne ou le produit interne généralisé avec la deuxième plage est à calculer.  
  
 `first2`  
 Itérateur d’entrée qui traite le premier élément de la deuxième plage dont le produit interne ou le produit interne généralisé avec la première plage est à calculer.  
  
 `val`  
 Valeur initiale à laquelle ajouter le produit interne ou le produit interne généralisé entre les plages.  
  
 *binary_op1*  
 Opération binaire qui remplace l’opération de somme du produit interne appliquée aux produits d’éléments dans la généralisation du produit interne.  
  
 *binary_op2*  
 Opération binaire qui remplace l’opération de multiplication des éléments du produit interne dans la généralisation du produit interne.  
  
### <a name="return-value"></a>Valeur de retour  
 La première fonction membre retourne la somme des produits d’éléments et y ajoute la valeur initiale spécifiée. Pour les plages de valeurs *a*i et *b*i, elle retourne :  
  
 `val`+ ( *a*1 \* *b*1 ) + ( *a*2 \* *b*2 ) + ... + ( *a*n \* *b*n ) 
  
 en remplaçant de manière itérative `val` avec `val` + ( *un*i \* *b*i).  
  
 La deuxième fonction membre retourne :  
  
 `val`*binary_op1* ( *a*1 *binary_op2* *b*1 ) *binary_op1* ( *a*2 *binary_op2* *b*2 ) *binary_op1* ... *binary_op1* ( *a*n *binary_op2* *b*n )  
  
 en remplaçant de manière itérative `val` avec `val` *binary_op1* ( *un*i *binary_op2* *b*i).  
  
### <a name="remarks"></a>Remarques  
 La valeur initiale garantit l’obtention d’un résultat bien défini quand la plage est vide, auquel cas `val` est retourné. Les opérations binaires ne sont pas tenues d’être associatives ou commutatives. La plage doit être valide et la complexité est linéaire par rapport à la taille de la plage. Le type de retour de l’opérateur binaire doit être convertible en **Type** pour assurer la fermeture pendant l’itération.  
  
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
  
##  <a name="iota"></a>  iota  
 Stocke une valeur de départ, en commençant par le premier élément et en remplissant la plage avec des incréments successifs de cette valeur ( ` value++`) dans chaque élément de l’intervalle `[ first,  last)`.  
  
```  
template <class ForwardIterator, class Type>  
void iota(ForwardIterator first, ForwardIterator last, Type value);
```  
  
### <a name="parameters"></a>Paramètres  
 `first`  
 Itérateur d’entrée qui traite le premier élément de la plage à remplir.  
  
 `last`  
 Itérateur d’entrée qui traite le dernier élément de la plage à remplir.  
  
 `value`  
 Valeur de départ à stocker dans le premier élément et à incrémenter successivement dans les éléments suivants.  
  
### <a name="remarks"></a>Notes  
  
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
  
##  <a name="partial_sum"></a>  partial_sum  
 Calcule une série de sommes dans une plage d’entrée à partir du premier élément jusqu’à l’élément numéro *i*, puis stocke le résultat de chaque somme dans l’élément numéro *i* d’une plage de destination, ou calcule le résultat d’une procédure généralisée où l’opération de somme est remplacée par une autre opération binaire spécifiée.  
  
```  
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
 `first`  
 Itérateur d'entrée qui traite le premier élément de la plage qui doit être partiellement additionné ou combiné, selon l'opération binaire spécifiée.  
  
 `last`  
 Itérateur d'entrée qui traite le dernier élément d'une plage qui doit être partiellement additionné ou combiné selon une opération binaire spécifiée, et dont la position se trouve immédiatement après le dernier élément inclus dans l'accumulation itérée.  
  
 `result`  
 Itérateur de sortie qui traite le premier élément d'une plage de destination dans laquelle les sommes partielles ou les résultats de l'opération spécifiée doivent être enregistrés.  
  
 `binary_op`  
 Opération binaire qui doit être appliquée dans l'opération généralisée par le remplacement de l'opération de somme de la procédure de somme partielle.    
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur de sortie qui traite la fin de la plage de destination : `result` + ( `last` - `first`),  
  
### <a name="remarks"></a>Notes  
 L'itérateur de sortie `result` peut être le même que l'itérateur d'entrée `first`, afin que les sommes partielles puissent être calculées sur place.  
  
 Pour une séquence de valeurs *a*1, *a*2, *a*3, dans une plage d’entrée, la première fonction de modèle stocke les sommes partielles successives dans la plage de destination, où l’élément numéro *i* est fourni par (  ( ( *a*1 + *a*2) + *a*3) *a*i).  
  
 Pour une séquence de valeurs *un*1, *un*2, *un*3, dans une plage d’entrée, la deuxième fonction de modèle stocke des sommes partielles successives dans la plage de destination, où l’élément ith est indiqué par ((( *un*1 `binary_op` *un*2) `binary_op` *un*3) *un*i).  
  
 Il n'est pas nécessaire que l'opération binaire `binary_op` soit associative ou commutative, car l'ordre des opérations appliqué est entièrement spécifié.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [\<numeric>](../standard-library/numeric.md)


