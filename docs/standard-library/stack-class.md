---
title: stack, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::stack
- std.stack
- stack
dev_langs:
- C++
helpviewer_keywords:
- stack, stack class
- stack class
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
caps.latest.revision: 22
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
ms.openlocfilehash: 81467a48b08fab628da94b217c2925010f3118fe
ms.lasthandoff: 02/24/2017

---
# <a name="stack-class"></a>stack, classe
Classe d'adaptateur de conteneur modèle qui fournit une restriction des fonctionnalités limitant l'accès à l'élément ajouté le plus récemment pour un type de conteneur sous-jacent. La classe stack est utilisée quand il est important de s'assurer que seules des opérations de pile sont effectuées sur le conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Type, class Container= deque <Type>>  
class stack  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Type*  
 Type de données des éléments à stocker dans la pile.  
  
 `Container`  
 Type du conteneur sous-jacent utilisé pour implémenter la pile. La valeur par défaut est la classe `deque`*\<Type>*.  
  
## <a name="remarks"></a>Notes  
 Les éléments de la classe **Type** stipulés dans le premier paramètre de modèle d’un objet stack sont synonymes de [value_type](#stack__value_type) et doivent correspondre au type d’élément de la classe de conteneur sous-jacent **Container** stipulé par le deuxième paramètre de modèle. La classe **Type** doit pouvoir faire l’objet d’une assignation, pour qu’il soit possible de copier des objets de ce type et d’assigner des valeurs aux variables de ce type.  
  
 Les classes de conteneur sous-jacent appropriées pour stack incluent la [classe deque](../standard-library/deque-class.md), la [classe list](../standard-library/list-class.md) et la [classe vector](../standard-library/vector-class.md) ou tout autre conteneur de séquence qui prend en charge les opérations **back**, `push_back` et `pop_back`. La classe de conteneur sous-jacent est encapsulée dans l'adaptateur de conteneur, qui expose seulement l'ensemble limité de fonctions membres du conteneur de séquence comme une interface publique.  
  
 Les objets stack sont comparables quant à l’égalité si et seulement si les éléments de la classe **Type** sont comparables quant à l’égalité, et ils sont comparables avec l’opérateur « inférieur à » si et seulement si les éléments de la classe **Type** sont comparables avec l’opérateur « inférieur à ».  
  
-   La classe stack prend en charge une structure de données LIFO (dernier entré, premier sorti). Une bonne analogie à avoir à l'esprit est celle d'une pile d'assiettes. Les éléments (les assiettes) peuvent être insérés, inspectés ou supprimés seulement à partir du haut de la pile, qui est le dernier élément à la fin du conteneur de base. La restriction qui fait que seul l'élément du haut est accessible est la raison de l'utilisation de la classe stack.  
  
-   La [classe queue](../standard-library/queue-class.md) prend en charge une structure de données FIFO (premier entré, premier sorti). Une bonne analogie à avoir à l'esprit est celle de personnes faisant la file pour un employé de banque. Les éléments (les personnes) peuvent être ajoutés à l'arrière de la file et ils sont supprimés de l'avant de la file. Le début et la fin d'une file peuvent être inspectés. La restriction qui fait que seuls les éléments de l'avant et de l'arrière sont accessibles de cette façon est la raison de l'utilisation de la classe queue.  
  
-   La [classe priority_queue](../standard-library/priority-queue-class.md) trie ses éléments pour que l’élément le plus grand soit toujours en haut. Elle prend en charge l'insertion d'un élément, et l'inspection et la suppression de l'élément du haut. Une bonne analogie à avoir à l'esprit est celle de personnes faisant la file, classées selon leur âge, leur taille ou un autre critère.  
  
### <a name="constructors"></a>Constructeurs  
  
|||  
|-|-|  
|[stack](#stack__stack)|Construit un objet `stack` qui est vide ou qui est une copie de l'objet conteneur de base.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#stack__container_type)|Type qui fournit le conteneur de base à adapter par un objet `stack`.|  
|[size_type](#stack__size_type)|Type entier non signé qui peut représenter le nombre d'éléments dans un `stack`.|  
|[value_type](#stack__value_type)|Type qui représente le type d'objet stocké en tant qu'élément dans un objet `stack`.|  
  
### <a name="member-functions"></a>Fonctions membres  
  
|||  
|-|-|  
|[empty](#stack__empty)|Vérifie si l'objet `stack` est vide.|  
|[pop](#stack__pop)|Supprime l'élément du haut de l'objet `stack`.|  
|[push](#stack__push)|Ajoute un élément en haut de l'objet `stack`.|  
|[size](#stack__size)|Retourne le nombre d'éléments d'un `stack`.|  
|[top](#stack__top)|Retourne une référence à un élément en haut de l'objet la`stack`.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<stack>  
  
 **Espace de noms :** std  
  
##  <a name="stack__container_type"></a>  stack::container_type  
 Type qui fournit le conteneur de base à adapter.  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Container`. Les trois classes de conteneur de séquence de la bibliothèque standard C++ (la classe vector, la classe list et la classe par défaut deque) remplissent les conditions pour être utilisées comme conteneur de base d’un objet stack. Les types définis par l’utilisateur peuvent également être utilisés s’ils remplissent ces conditions.  
  
 Pour plus d’informations sur `Container`, consultez la section Notes de la rubrique [stack, classe](../standard-library/stack-class.md).  
  
### <a name="example"></a>Exemple  
  Pour savoir comment déclarer et utiliser `container_type`, consultez l’exemple [stack::stack](#stack__stack).  
  
##  <a name="stack__empty"></a>  stack::empty  
 Vérifie si un objet stack est vide.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’objet stack est vide. **false** s’il n’est pas vide.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// stack_empty.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // Declares stacks with default deque base container  
   stack <int> s1, s2;  
  
   s1.push( 1 );  
  
   if ( s1.empty( ) )  
      cout << "The stack s1 is empty." << endl;  
   else  
      cout << "The stack s1 is not empty." << endl;  
  
   if ( s2.empty( ) )  
      cout << "The stack s2 is empty." << endl;  
   else  
      cout << "The stack s2 is not empty." << endl;  
}  
```  
  
```Output  
The stack s1 is not empty.  
The stack s2 is empty.  
```  
  
##  <a name="stack__pop"></a>  stack::pop  
 Supprime l’élément du haut de l’objet stack.  
  
```  
void pop();
```  
  
### <a name="remarks"></a>Notes  
 L’objet stack ne doit pas être vide pour appliquer la fonction membre. Le haut de l’objet stack correspond à la position occupée par l’élément ajouté le plus récemment et au dernier élément à la fin du conteneur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// stack_pop.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1, s2;  
  
   s1.push( 10 );  
   s1.push( 20 );  
   s1.push( 30 );  
  
   stack <int>::size_type i;  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   i = s1.top( );  
   cout << "The element at the top of the stack is "  
        << i << "." << endl;  
  
   s1.pop( );  
  
   i = s1.size( );  
   cout << "After a pop, the stack length is "   
        << i << "." << endl;  
  
   i = s1.top( );  
   cout << "After a pop, the element at the top of the stack is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 3.  
The element at the top of the stack is 30.  
After a pop, the stack length is 2.  
After a pop, the element at the top of the stack is 20.  
```  
  
##  <a name="stack__push"></a>  stack::push  
 Ajoute un élément tout en haut de l’objet stack.  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>Paramètres  
 `val`  
 Élément ajouté en haut de l’objet stack.  
  
### <a name="remarks"></a>Notes  
 Le haut de l’objet stack correspond à la position occupée par l’élément ajouté le plus récemment et au dernier élément à la fin du conteneur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// stack_push.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1;  
  
   s1.push( 10 );  
   s1.push( 20 );  
   s1.push( 30 );  
  
   stack <int>::size_type i;  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   i = s1.top( );  
   cout << "The element at the top of the stack is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 3.  
The element at the top of the stack is 30.  
```  
  
##  <a name="stack__size"></a>  stack::size  
 Retourne le nombre d’éléments figurant dans l’objet stack.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Longueur actuelle de l’objet stack.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// stack_size.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1, s2;  
   stack <int>::size_type i;  
  
   s1.push( 1 );  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   s1.push( 2 );  
   i = s1.size( );  
   cout << "The stack length is now " << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 1.  
The stack length is now 2.  
```  
  
##  <a name="stack__size_type"></a>  stack::size_type  
 Type entier non signé qui peut représenter le nombre d’éléments dans un objet stack.  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme de `size_type` pour le conteneur de base adapté par la classe stack.  
  
### <a name="example"></a>Exemple  
  Pour savoir comment déclarer et utiliser `size_type`, consultez l’exemple [size](#stack__size).  
  
##  <a name="stack__stack"></a>  stack::stack  
 Construit un objet stack qui est vide ou qui est une copie d’une classe de conteneur de base.  
  
```  
stack();

explicit stack(const container_type& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `right`  
 Conteneur dont l’objet stack construit doit être une copie.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// stack_stack.cpp  
// compile with: /EHsc  
#include <stack>  
#include <vector>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares stack with default deque base container  
   stack <char> dsc1;  
  
   //Explicitly declares a stack with deque base container  
   stack <char, deque<char> > dsc2;  
  
   // Declares a stack with vector base containers  
   stack <int, vector<int> > vsi1;  
  
   // Declares a stack with list base container  
   stack <int, list<int> > lsi;  
  
   // The second member function copies elements from a container  
   vector<int> v1;  
   v1.push_back( 1 );  
   stack <int, vector<int> > vsi2( v1 );  
   cout << "The element at the top of stack vsi2 is "  
        << vsi2.top( ) << "." << endl;  
}  
```  
  
```Output  
The element at the top of stack vsi2 is 1.  
```  
  
##  <a name="stack__top"></a>  stack::top  
 Retourne une référence à un élément en haut de l’objet stack.  
  
```  
reference top();

const_reference top() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Référence au dernier élément dans le conteneur en haut de l’objet stack.  
  
### <a name="remarks"></a>Notes  
 L’objet stack ne doit pas être vide pour appliquer la fonction membre. Le haut de l’objet stack correspond à la position occupée par l’élément ajouté le plus récemment et au dernier élément à la fin du conteneur.  
  
 Si la valeur de retour de **top** est assignée à `const_reference`, l’objet stack ne peut pas être modifié. Si la valeur de retour de **top** est assignée à **reference**, l’objet stack peut être modifié.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// stack_top.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1;  
  
   s1.push( 1 );  
   s1.push( 2 );  
  
   int& i = s1.top( );  
   const int& ii = s1.top( );  
  
   cout << "The top integer of the stack s1 is "  
        << i << "." << endl;  
   i--;  
   cout << "The next integer down is "<< ii << "." << endl;  
}  
```  
  
```Output  
The top integer of the stack s1 is 2.  
The next integer down is 1.  
```  
  
##  <a name="stack__value_type"></a>  stack::value_type  
 Type qui représente le type d’objet stocké comme élément dans une classe stack.  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme de `value_type` pour le conteneur de base adapté par la classe stack.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// stack_value_type.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // Declares stacks with default deque base container  
   stack<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   stack<int> s1;  
   s1.push( AnInt );  
   cout << "The element at the top of the stack is "  
        << s1.top( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the top of the stack is 69.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)


