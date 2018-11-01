---
title: stack, classe
ms.date: 11/04/2016
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
helpviewer_keywords:
- std::stack [C++], container_type
- std::stack [C++], size_type
- std::stack [C++], value_type
- std::stack [C++], empty
- std::stack [C++], pop
- std::stack [C++], push
- std::stack [C++], size
- std::stack [C++], top
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
ms.openlocfilehash: cc18a62db3f39bc85c0a3bb7e84e6a27011c2b5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437386"
---
# <a name="stack-class"></a>stack, classe

Classe d'adaptateur de conteneur modèle qui fournit une restriction des fonctionnalités limitant l'accès à l'élément ajouté le plus récemment pour un type de conteneur sous-jacent. La classe stack est utilisée quand il est important de s'assurer que seules des opérations de pile sont effectuées sur le conteneur.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>Paramètres

*Type*<br/>
Type de données des éléments à stocker dans la pile.

*Conteneur*<br/>
Type du conteneur sous-jacent utilisé pour implémenter la pile. La valeur par défaut est la classe `deque`*\<Type>*.

## <a name="remarks"></a>Notes

Les éléments de classe `Type` stipulés dans le modèle de paramètre d’un objet stack sont synonymes de [value_type](#value_type) et doit correspondre au type d’élément de la classe de conteneur sous-jacent `Container` stipulé par le deuxième paramètre de modèle. Le `Type` doit être assignable, afin qu’il soit possible de copier des objets de ce type et d’affecter des valeurs aux variables de ce type.

Classes de conteneur sous-jacent appropriées pour stack incluent [deque](../standard-library/deque-class.md), [list, classe](../standard-library/list-class.md), et [vector, classe](../standard-library/vector-class.md), ou tout autre conteneur de séquence qui prend en charge les opérations de `back`, `push_back`, et `pop_back`. La classe de conteneur sous-jacent est encapsulée dans l'adaptateur de conteneur, qui expose seulement l'ensemble limité de fonctions membres du conteneur de séquence comme une interface publique.

Les objets stack sont comparables à l’égalité si et seulement si les éléments de classe `Type` l’égalité ne sont comparables, et ils inférieur-que comparable si et seulement si les éléments de classe `Type` sont inférieurs-que comparable.

- La classe stack prend en charge une structure de données LIFO (dernier entré, premier sorti). Une bonne analogie à avoir à l'esprit est celle d'une pile d'assiettes. Les éléments (les assiettes) peuvent être insérés, inspectés ou supprimés seulement à partir du haut de la pile, qui est le dernier élément à la fin du conteneur de base. La restriction qui fait que seul l'élément du haut est accessible est la raison de l'utilisation de la classe stack.

- La [classe queue](../standard-library/queue-class.md) prend en charge une structure de données FIFO (premier entré, premier sorti). Une bonne analogie à avoir à l'esprit est celle de personnes faisant la file pour un employé de banque. Les éléments (les personnes) peuvent être ajoutés à l'arrière de la file et ils sont supprimés de l'avant de la file. Le début et la fin d'une file peuvent être inspectés. La restriction qui fait que seuls les éléments de l'avant et de l'arrière sont accessibles de cette façon est la raison de l'utilisation de la classe queue.

- La [classe priority_queue](../standard-library/priority-queue-class.md) trie ses éléments pour que l’élément le plus grand soit toujours en haut. Elle prend en charge l'insertion d'un élément, et l'inspection et la suppression de l'élément du haut. Une bonne analogie à avoir à l'esprit est celle de personnes faisant la file, classées selon leur âge, leur taille ou un autre critère.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[stack](#stack)|Construit un objet `stack` qui est vide ou qui est une copie de l'objet conteneur de base.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[container_type](#container_type)|Type qui fournit le conteneur de base à adapter par un objet `stack`.|
|[size_type](#size_type)|Type entier non signé qui peut représenter le nombre d'éléments dans un `stack`.|
|[value_type](#value_type)|Type qui représente le type d'objet stocké en tant qu'élément dans un objet `stack`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[empty](#empty)|Vérifie si l'objet `stack` est vide.|
|[pop](#pop)|Supprime l'élément du haut de l'objet `stack`.|
|[push](#push)|Ajoute un élément en haut de l'objet `stack`.|
|[size](#size)|Retourne le nombre d'éléments d'un `stack`.|
|[top](#top)|Retourne une référence à un élément en haut de l'objet la`stack`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<stack>

**Espace de noms :** std

## <a name="container_type"></a>  stack::container_type

Type qui fournit le conteneur de base à adapter.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Container`. Les trois classes de conteneur de séquence de la bibliothèque standard C++ (la classe vector, la classe list et la classe par défaut deque) remplissent les conditions pour être utilisées comme conteneur de base d’un objet stack. Les types définis par l’utilisateur peuvent également être utilisés s’ils remplissent ces conditions.

Pour plus d’informations sur `Container`, consultez la section Notes de la rubrique [stack, classe](../standard-library/stack-class.md).

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `container_type`, consultez l’exemple [stack::stack](#stack).

## <a name="empty"></a>  stack::empty

Vérifie si un objet stack est vide.

```cpp
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

## <a name="pop"></a>  stack::pop

Supprime l’élément du haut de l’objet stack.

```cpp
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

## <a name="push"></a>  stack::push

Ajoute un élément vers le haut de la pile.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Paramètres

*Val*<br/>
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

## <a name="size"></a>  stack::size

Retourne le nombre d’éléments figurant dans l’objet stack.

```cpp
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

## <a name="size_type"></a>  stack::size_type

Type entier non signé qui peut représenter le nombre d’éléments dans un objet stack.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `size_type` pour le conteneur de base adapté par la classe stack.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `size_type`, consultez l’exemple [size](#size).

## <a name="stack"></a>  stack::stack

Construit un objet stack qui est vide ou qui est une copie d’une classe de conteneur de base.

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
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

## <a name="top"></a>  stack::top

Retourne une référence à un élément en haut de l’objet stack.

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>Valeur de retour

Référence au dernier élément dans le conteneur en haut de l’objet stack.

### <a name="remarks"></a>Notes

L’objet stack ne doit pas être vide pour appliquer la fonction membre. Le haut de l’objet stack correspond à la position occupée par l’élément ajouté le plus récemment et au dernier élément à la fin du conteneur.

Si la valeur de retour de `top` est affecté à un `const_reference`, l’objet de pile ne peut pas être modifié. Si la valeur de retour de `top` est affecté à un `reference`, l’objet de pile peut être modifié.

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

## <a name="value_type"></a>  stack::value_type

Type qui représente le type d’objet stocké comme élément dans une classe stack.

```cpp
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

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
