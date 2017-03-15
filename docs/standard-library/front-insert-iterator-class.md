---
title: front_insert_iterator, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iterator/std::front_insert_iterator
- std::front_insert_iterator
- std.front_insert_iterator
- front_insert_iterator
dev_langs:
- C++
helpviewer_keywords:
- front_insert_iterator class
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 6468f372324cb6f62b5b09524cfbf5386b1502c6
ms.lasthandoff: 02/24/2017

---
# <a name="frontinsertiterator-class"></a>front_insert_iterator, classe
Décrit un adaptateur d’itérateur qui répond aux exigences d’un itérateur de sortie. Elle insère, plutôt que remplace, des éléments du début d'une séquence et fournit ainsi une sémantique différente de la sémantique de remplacement fournie par les itérateurs des conteneurs de la séquence C++. La classe `front_insert_iterator` est mise en modèle d'après le type de conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Container>  
class front_insert_iterator;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Container`  
 Type de conteneur au début duquel des éléments doivent être insérés par un `front_insert_iterator`.  
  
## <a name="remarks"></a>Notes  
 Le conteneur doit répondre aux exigences d’une insertion de début de séquence où il est possible d’insérer des éléments au début de la séquence dans le temps fixe amorti. Les conteneurs de séquence de bibliothèque C++ Standard définis par la [classe deque](../standard-library/deque-class.md) et la [classe list](../standard-library/list-class.md) fournissent la fonction membre `push_front` nécessaire et répondent à ces exigences. En revanche, les conteneurs de séquence définis par la [classe vector](../standard-library/vector-class.md) ne répondent pas à ces exigences et ne peuvent pas être adaptés pour être utilisés avec des `front_insert_iterator`. Un `front_insert_iterator` doit toujours être initialisé avec son conteneur.  
  
### <a name="constructors"></a>Constructeurs  
  
|||  
|-|-|  
|[front_insert_iterator](#front_insert_iterator__front_insert_iterator)|Crée un itérateur qui peut insérer des éléments au début d'un objet conteneur spécifié.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#front_insert_iterator__container_type)|Type qui représente le conteneur dans lequel une insertion de début doit être effectuée.|  
|[reference](#front_insert_iterator__reference)|Type qui fournit une référence à un élément dans une séquence contrôlée par le conteneur associé.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[operator*](#front_insert_iterator__operator_star)|Opérateur de suppression de référence utilisé pour implémenter l’expression de l’itérateur de sortie * `i` = `x` pour une insertion de début.|  
|[operator++](#front_insert_iterator__operator_add_add)|Incrémente le `front_insert_iterator` à l'emplacement suivant où une valeur peut être stockée.|  
|[operator=](#front_insert_iterator__operator_eq)|Opérateur d’assignation servant à implémenter l’expression de l’itérateur de sortie * `i` = `x` pour une insertion de début.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête** : \<iterator>  
  
 **Espace de noms :** std  
  
##  <a name="a-namefrontinsertiteratorcontainertypea--frontinsertiteratorcontainertype"></a><a name="front_insert_iterator__container_type"></a>  front_insert_iterator::container_type  
 Type qui représente le conteneur dans lequel une insertion de début doit être effectuée.  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle **Container**.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// front_insert_iterator_container_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> >::container_type L2 = L1;  
   front_inserter ( L2 ) = 20;  
   front_inserter ( L2 ) = 10;  
   front_inserter ( L2 ) = 40;  
  
   list <int>::iterator vIter;  
   cout << "The list L2 is: ( ";  
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L2 is: ( 40 10 20 ).  
*\  
```  
  
##  <a name="a-namefrontinsertiteratorfrontinsertiteratora--frontinsertiteratorfrontinsertiterator"></a><a name="front_insert_iterator__front_insert_iterator"></a>  front_insert_iterator::front_insert_iterator  
 Crée un itérateur qui peut insérer des éléments au début d'un objet conteneur spécifié.  
  
```  
explicit front_insert_iterator(Container& _Cont);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Cont`  
 Objet de conteneur dans lequel `front_insert_iterator` doit insérer des éléments.  
  
### <a name="return-value"></a>Valeur de retour  
 `front_insert_iterator` pour l’objet conteneur du paramètre.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// front_insert_iterator_front_insert_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for (i = -1 ; i < 9 ; ++i )    
   {  
      L.push_back ( 2 * i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   // Using the member function to insert an element  
   front_inserter ( L ) = 20;  
  
   // Alternatively, one may use the template function  
   front_insert_iterator< list < int> > Iter(L);  
 *Iter = 30;  
  
   cout << "After the front insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L is:  
 ( -2 0 2 4 6 8 10 12 14 16 ).  
After the front insertions, the list L is:  
 ( 30 20 -2 0 2 4 6 8 10 12 14 16 ).  
*\  
```  
  
##  <a name="a-namefrontinsertiteratoroperatorstara--frontinsertiteratoroperator"></a><a name="front_insert_iterator__operator_star"></a>  front_insert_iterator::operator*  
 Supprime la référence à l’itérateur d’insertion retournant l’élément ciblé.  
  
```  
front_insert_iterator<Container>& operator*();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La fonction membre retourne la valeur de l’élément ciblé.  
  
### <a name="remarks"></a>Notes  
 Utilisé pour implémenter l’expression d’itérateur de sortie **\*Iter** = **value**. Si **Iter** est un itérateur qui cible un élément dans une séquence, alors **\*Iter** = **value** remplace cet élément par value et ne change pas le nombre total d’éléments dans la séquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// front_insert_iterator_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for ( i = -1 ; i < 9 ; ++i )   
   {  
      L.push_back ( 2 * i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   front_insert_iterator< list < int> > Iter(L);  
 *Iter = 20;  
  
   // Alternatively, you may use  
   front_inserter ( L ) = 30;  
  
   cout << "After the front insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L is:  
 ( -2 0 2 4 6 8 10 12 14 16 ).  
After the front insertions, the list L is:  
 ( 30 20 -2 0 2 4 6 8 10 12 14 16 ).  
*\  
```  
  
##  <a name="a-namefrontinsertiteratoroperatoraddadda--frontinsertiteratoroperator"></a><a name="front_insert_iterator__operator_add_add"></a>  front_insert_iterator::operator++  
 Incrémente le `back_insert_iterator` à l'emplacement suivant où une valeur peut être stockée.  
  
```  
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```  
  
### <a name="return-value"></a>Valeur de retour  
 `front_insert_iterator` qui cible l’emplacement suivant où une valeur peut être stockée.  
  
### <a name="remarks"></a>Notes  
 Les opérateurs de préincrémentation et de postincrémentation retournent le même résultat.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// front_insert_iterator_op_incre.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> > iter ( L1 );  
 *iter = 10;  
   iter++;  
 *iter = 20;  
   iter++;  
 *iter = 30;  
   iter++;  
  
   list <int>::iterator vIter;  
   cout << "The list L1 is: ( ";  
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L1 is: ( 30 20 10 ).  
*\  
```  
  
##  <a name="a-namefrontinsertiteratoroperatoreqa--frontinsertiteratoroperator"></a><a name="front_insert_iterator__operator_eq"></a>  front_insert_iterator::operator=  
 Ajoute (push) une valeur au début du conteneur.  
  
```  
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```  
  
### <a name="parameters"></a>Paramètres  
 ` val`  
 Valeur à assigner au conteneur.  
  
### <a name="return-value"></a>Valeur de retour  
 Référence au dernier élément inséré au début du conteneur.  
  
### <a name="remarks"></a>Notes  
 Le premier opérateur membre évalue `container.push_front( val)`, puis retourne `*this`.  
  
 Le deuxième opérateur membre évalue  
  
 `container->push_front((typename Container::value_type&&) val)`,  
  
 puis retourne `*this`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// front_insert_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> > iter ( L1 );  
 *iter = 10;  
   iter++;  
 *iter = 20;  
   iter++;  
 *iter = 30;  
   iter++;  
  
   list <int>::iterator vIter;  
   cout << "The list L1 is: ( ";  
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L1 is: ( 30 20 10 ).  
*\  
```  
  
##  <a name="a-namefrontinsertiteratorreferencea--frontinsertiteratorreference"></a><a name="front_insert_iterator__reference"></a>  front_insert_iterator::reference  
 Type qui fournit une référence à un élément dans une séquence contrôlée par le conteneur associé.  
  
```  
typedef typename Container::reference reference;  
```  
  
### <a name="example"></a>Exemple  
  
```cpp  
// front_insert_iterator_reference.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L;  
   front_insert_iterator<list<int> > fiivIter( L );  
 *fiivIter = 10;  
 *fiivIter = 20;  
 *fiivIter = 30;  
  
   list<int>::iterator LIter;  
   cout << "The list L is: ( ";  
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)  
      cout << *LIter << " ";  
   cout << ")." << endl;  
  
   front_insert_iterator<list<int> >::reference   
        RefFirst = *(L.begin ( ));  
   cout << "The first element in the list L is: "   
        << RefFirst << "." << endl;  
}  
\* Output:   
The list L is: ( 30 20 10 ).  
The first element in the list L is: 30.  
*\  
```  
  
## <a name="see-also"></a>Voir aussi  
 [\<iterator>](../standard-library/iterator.md)   
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)


