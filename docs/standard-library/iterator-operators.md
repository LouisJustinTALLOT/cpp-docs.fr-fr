---
title: "&lt;iterator&gt;, opérateurs | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xutility/std::operator!=
- xutility/std::operator&gt;
- xutility/std::operator&gt;=
- xutility/std::operator&lt;
- xutility/std::operator&lt;=
- xutility/std::operator+
- xutility/std::operator-
- xutility/std::operator==
dev_langs: C++
ms.assetid: b7c664f0-49d4-4993-b5d1-9ac4859fdddc
caps.latest.revision: "10"
manager: ghogen
helpviewer_keywords:
- std::operator!= (iterator)
- std::operator&gt; (iterator)
- std::operator&gt;= (iterator)
- std::operator&lt; (iterator)
- std::operator&lt;= (iterator), std::operator== (iterator)
ms.openlocfilehash: a6e5d30b970c3887c9ac7641ec39275acd9cd79d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="ltiteratorgt-operators"></a>&lt;iterator&gt;, opérateurs
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator+](#op_add)|  
|[operator-](#operator-)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  operator!=  
 Teste si l'objet itérateur situé à gauche de l'opérateur n'est pas égal à l'objet itérateur situé à droite.  
  
```  
template <class RandomIterator>  
bool operator!=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);

template <class Type, class CharType, class Traits, class Distance>  
bool operator!=(const istream_iterator<Type, CharType, Traits, Distance>& left, const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>  
bool operator!=(const istreambuf_iterator<CharType, Traits>& left, const istreambuf_iterator<CharType, Traits>& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type **iterator**.  
  
 `right`  
 Objet de type **iterator**.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si les objets itérateurs ne sont pas égaux ; **false** si les objets itérateurs sont égaux.  
  
### <a name="remarks"></a>Notes  
 Un objet itérateur est égal à un autre s’ils traitent les mêmes éléments dans un conteneur. Si deux itérateurs pointent vers différents éléments dans un conteneur, ils sont inégaux.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// iterator_op_ne.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 9 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 != rVPOS2 )  
      cout << "The iterators are not equal." << endl;  
   else  
      cout << "The iterators are equal." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 != rVPOS2 )  
      cout << "The iterators are not equal." << endl;  
   else  
      cout << "The iterators are equal." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 2 3 4 5 6 7 8 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 8.  
The iterators are equal.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 7.  
The iterators are not equal.  
```  
  
##  <a name="op_eq_eq"></a>  operator==  
 Teste si l'objet itérateur situé à gauche de l'opérateur est égal à l'objet itérateur situé à droite.  
  
```  
template <class RandomIterator1, class RandomIterator2>  
bool operator==(
    const move_iterator<RandomIterator1>& left,  
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>  
bool operator==(
    const reverse_iterator<RandomIterator1>& left,  
    const reverse_iterator<RandomIterator2>& right);

template <class Type, class CharType, class Traits, class Distance>  
bool operator==(
    const istream_iterator<Type, CharType, Traits, Distance>& left,  
    const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>  
bool operator==(
    const istreambuf_iterator<CharType, Traits>& left,  
    const istreambuf_iterator<CharType, Traits>& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type iterator.  
  
 `right`  
 Objet de type iterator.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si les objets itérateurs sont égaux ; `false` si les objets itérateurs ne sont pas égaux.  
  
### <a name="remarks"></a>Notes  
 Un objet itérateur est égal à un autre s’ils traitent les mêmes éléments dans un conteneur. Si deux itérateurs pointent vers différents éléments dans un conteneur, ils sont inégaux.  
  
 Les deux premiers opérateurs de modèle retournent true uniquement si `left` et `right` stockent le même itérateur. Le troisième opérateur de modèle retourne true uniquement si `left` et `right` stockent le même pointeur de flux. Le quatrième opérateur de modèle retourne ` left.equal ( right)`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// iterator_op_eq.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 6 ; ++i )  
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 == rVPOS2 )  
      cout << "The iterators are equal." << endl;  
   else  
      cout << "The iterators are not equal." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 == rVPOS2 )  
      cout << "The iterators are equal." << endl;  
   else  
      cout << "The iterators are not equal." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterators are equal.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterators are not equal.  
```  
  
##  <a name="op_lt"></a>  operator&lt;  
 Teste si l'objet itérateur situé à gauche de l'opérateur est inférieur à l'objet itérateur situé à droite.  
  
```  
template <class RandomIterator>  
bool operator<(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type **iterator**.  
  
 `right`  
 Objet de type **iterator**.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’itérateur du côté gauche de l’expression est inférieur à l’itérateur du côté droit de l’expression ; **false** s’il est supérieur ou égal à l’itérateur de droite.  
  
### <a name="remarks"></a>Notes  
 Un objet itérateur est inférieur à un autre s’il traite un élément qui se produit plus tôt dans le conteneur que l’élément traité par l’autre objet itérateur. Un objet itérateur n’est pas inférieur à un autre s’il traite soit le même élément que l’autre objet itérateur, soit un élément qui se produit plus loin dans le conteneur que l’élément traité par l’autre objet itérateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// iterator_op_lt.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 0 ; i < 6 ; ++i )  
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1& rVPOS2 initially point to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 < rVPOS2 )  
      cout << "The iterator rVPOS1 is less than"  
              << " the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is not less than"  
              << " the iterator rVPOS2." << endl;  
  
   rVPOS2++;  
   cout << "The iterator rVPOS2 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 < rVPOS2 )  
      cout << "The iterator rVPOS1 is less than"  
              << " the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is not less than"  
              << " the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1& rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is not less than the iterator rVPOS2.  
The iterator rVPOS2 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than the iterator rVPOS2.  
```  
  
##  <a name="op_lt_eq"></a>  operator&lt;=  
 Teste si l'objet itérateur situé à gauche de l'opérateur est inférieur ou égal à l'objet itérateur situé à droite.  
  
```  
template <class RandomIterator>  
bool operator<=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type iterator.  
  
 `right`  
 Objet de type iterator.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’itérateur du côté gauche de l’expression est inférieur ou égal à l’itérateur du côté droit de l’expression ; **false** s’il est supérieur à l’itérateur de droite.  
  
### <a name="remarks"></a>Notes  
 Un objet itérateur est inférieur ou égal à un autre s’il traite le même élément ou un élément qui se produit plus tôt dans le conteneur que l’élément traité par l’autre objet itérateur. Un objet itérateur est supérieur à un autre s’il traite un élément qui se produit plus loin dans le conteneur que l’élément traité par l’autre objet itérateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// iterator_op_le.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ) + 1,   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the "  
           << "second element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   cout << "The iterator rVPOS2 initially points to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 <= rVPOS2 )  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
  
   rVPOS2++;  
   cout << "The iterator rVPOS2 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 <= rVPOS2 )  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS2 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is greater than the iterator rVPOS2.  
The iterator rVPOS2 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.  
```  
  
##  <a name="op_gt"></a>  operator&gt;  
 Teste si l'objet itérateur situé à gauche de l'opérateur est supérieur à l'objet itérateur situé à droite.  
  
```  
template <class RandomIterator>  
bool operator>(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type iterator.  
  
 `right`  
 Objet de type iterator.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’itérateur du côté gauche de l’expression est supérieur à l’itérateur du côté droit de l’expression ; **false** s’il est inférieur ou égal à l’itérateur de droite.  
  
### <a name="remarks"></a>Notes  
 Un objet itérateur est supérieur à un autre s’il traite un élément qui se produit plus loin dans le conteneur que l’élément traité par l’autre objet itérateur. Un objet itérateur n’est pas supérieur à un autre s’il traite soit le même élément que l’autre objet itérateur, soit un élément qui se produit plus tôt dans le conteneur que l’élément traité par l’autre objet itérateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// iterator_op_gt.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1 & rVPOS2 initially point to "  
           << "the first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 > rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 > rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1 & rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is greater than the iterator rVPOS2.  
```  
  
##  <a name="op_gt_eq"></a>  operator&gt;=  
 Teste si l'objet itérateur situé à gauche de l'opérateur est supérieur ou égal à l'objet itérateur situé à droite.  
  
```  
template <class RandomIterator>  
bool operator>=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type iterator.  
  
 `right`  
 Objet de type iterator.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’itérateur du côté gauche de l’expression est supérieur ou égal à l’itérateur du côté droit de l’expression ; **false** s’il est inférieur à l’itérateur de droite.  
  
### <a name="remarks"></a>Notes  
 Un objet itérateur est supérieur ou égal à un autre s’il traite le même élément ou un élément qui se produit plus loin dans le conteneur que l’élément traité par l’autre objet itérateur. Un objet itérateur est inférieur à un autre s’il traite un élément qui se produit plus tôt dans le conteneur que l’élément traité par l’autre objet itérateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// iterator_op_ge.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( ) + 1;  
  
   cout << "The iterator rVPOS1 initially points to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   cout << "The iterator rVPOS2 initially points to the "  
           << "second element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 >= rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than "  
              << "the iterator rVPOS2." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 >= rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than "  
              << "the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS2 initially points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than the iterator rVPOS2.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is greater than or equal to the iterator rVPOS2.  
```  
  
##  <a name="op_add"></a>  operator+  
 Ajoute un décalage à un itérateur et retourne un `move_iterator` ou `reverse_iterator` qui traite l’élément inséré à la nouvelle position décalée.  
  
```  
template <class RandomIterator, class Diff>  
move_iterator<RandomIterator>  
operator+(
    Diff _Off,  
    const move_iterator<RandomIterator>& right);

template <class RandomIterator>  
reverse_iterator<RandomIterator>  
operator+(
    Diff _Off,  
    const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Off`  
 Nombre de positions duquel décaler le const move_iterator ou const reverse_iterator.  
  
 `right`  
 Itérateur à décaler.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la somme `right` + `_Off`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// iterator_op_insert.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to "  
           << "the first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   vector<int>::difference_type diff = 4;  
   rVPOS1 = diff +rVPOS1;  
  
   cout << "The iterator rVPOS1 now points to the fifth "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 now points to the fifth element  
 in the reversed sequence: 2.  
```  
  
##  <a name="operator-"></a>  operator-  
 Soustrait un itérateur à un autre et retourne la différence.  
  
```  
template <class RandomIterator1, class RandomIterator2>  
Tdiff operator-(
    const move_iterator<RandomIterator1>& left,  
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>  
Tdiff operator-(
    const reverse_iterator<RandomIterator1>& left,  
    const reverse_iterator<RandomIterator2>& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Itérateur.  
  
 `right`  
 Itérateur.  
  
### <a name="return-value"></a>Valeur de retour  
 Différence entre deux itérateurs `.`.  
  
### <a name="remarks"></a>Notes  
 Le premier opérateur de modèle retourne `left.base() - right.base()`.  
  
 Le deuxième opérateur de modèle retourne `right.current - left.current`.  
  
 `Tdiff` est déterminé par le type de l’expression retournée. Sinon, il s'agit de `RandomIterator1::difference_type`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// iterator_op_sub.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )    
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
          rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1 & rVPOS2 initially point to "  
        << "the first element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   for (i = 1; i < 5; ++i)    
   {  
      rVPOS2++;  
   }  
   cout << "The iterator rVPOS2 now points to the fifth "  
        << "element\n in the reversed sequence: "  
        << *rVPOS2 << "." << endl;  
  
   vector<int>::difference_type diff = rVPOS2 - rVPOS1;  
   cout << "The difference: rVPOS2 - rVPOS1= "  
        << diff << "." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1 & rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS2 now points to the fifth element  
 in the reversed sequence: 2.  
The difference: rVPOS2 - rVPOS1= 4.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [\<iterator>](../standard-library/iterator.md)

