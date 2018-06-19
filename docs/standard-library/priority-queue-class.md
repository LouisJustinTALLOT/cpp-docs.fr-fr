---
title: priority_queue, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
dev_langs:
- C++
helpviewer_keywords:
- std::priority_queue [C++], container_type
- std::priority_queue [C++], size_type
- std::priority_queue [C++], value_type
- std::priority_queue [C++], empty
- std::priority_queue [C++], pop
- std::priority_queue [C++], push
- std::priority_queue [C++], size
- std::priority_queue [C++], top
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 149d255dd82d0dff2d2ddb1101b38bf05c69673a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861914"
---
# <a name="priorityqueue-class"></a>priority_queue, classe

Classe d’adaptateur de conteneur de modèle qui fournit une restriction de fonctionnalité limitant l’accès à l’élément supérieur d’un certain type de conteneur sous-jacent, qui est toujours le plus grand ou de la priorité la plus élevée. De nouveaux éléments peuvent être ajoutés à la classe priority_queue, et l’élément supérieur dans priority_queue peut être inspecté ou supprimé.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>Paramètres

*Type* type de données de l’élément à stocker dans le priority_queue.

`Container` Le type du conteneur sous-jacent utilisé pour implémenter le priority_queue.

*Comparer* le type qui fournit un objet de fonction qui peut comparer deux valeurs d’éléments comme clés de tri pour déterminer leur ordre relatif dans le priority_queue. Cet argument est facultatif et le prédicat binaire **moins***\<*** typename** *conteneur ***:: value_type*** >* est la valeur par défaut.

## <a name="remarks"></a>Notes

Les éléments de la classe **Type** stipulés dans le premier paramètre de modèle d’un objet queue sont synonymes de [value_type](#value_type) et doivent correspondre au type d’élément de la classe de conteneur sous-jacent **Container** stipulé par le deuxième paramètre de modèle. La classe **Type** doit pouvoir faire l’objet d’une assignation, pour qu’il soit possible de copier des objets de ce type et d’assigner des valeurs aux variables de ce type.

La classe priority_queue trie la séquence qu’elle contrôle en appelant un objet de fonction stocké de la classe **Traits**. En général, les éléments ne doivent pas être tout à fait comparables, afin que, à l'aide de deux événements quelconques donnés, il soit possible de déterminer, soit qu'ils soient équivalents (dans le sens où l'un n'est pas inférieur à l'autre), soit que l'un est inférieur à l'autre. Cela entraîne le tri des éléments non équivalents. D’un point de vue plus technique, la fonction de comparaison est un prédicat binaire qui induit un ordre faible strict au sens mathématique du terme.

Les classes de conteneurs sous-jacents appropriées pour priority_queue incluent la [classe deque](../standard-library/deque-class.md) et la [classe vector](../standard-library/vector-class.md) par défaut ou tout autre conteneur de séquence qui prend en charge les opérations `front`, `push_back` et `pop_back` ainsi qu’un itérateur à accès aléatoire. La classe de conteneur sous-jacent est encapsulée dans l'adaptateur de conteneur, qui expose seulement l'ensemble limité de fonctions membres du conteneur de séquence comme une interface publique.

L’ajout et la suppression d’éléments dans une classe `priority_queue` présentent une complexité logarithmique. L’accès aux éléments dans une classe `priority_queue` présente une complexité constante.

Il y a trois types d’adaptateurs de conteneur définis dans la bibliothèque standard C++ : stack, queue et priority_queue. Chaque type limite les fonctionnalités d’une classe de conteneur sous-jacent pour fournir une interface contrôlée de façon précise à une structure de données standard.

- La [classe stack](../standard-library/stack-class.md) prend en charge une structure de données LIFO (dernier entré, premier sorti). Une bonne analogie à avoir à l'esprit est celle d'une pile d'assiettes. Les éléments (les assiettes) peuvent être insérés, inspectés ou supprimés seulement à partir du haut de la pile, qui est le dernier élément à la fin du conteneur de base. La restriction qui fait que seul l'élément du haut est accessible est la raison de l'utilisation de la classe stack.

- La [classe queue](../standard-library/queue-class.md) prend en charge une structure de données FIFO (premier entré, premier sorti). Une bonne analogie à avoir à l'esprit est celle de personnes faisant la file pour un employé de banque. Les éléments (les personnes) peuvent être ajoutés à l'arrière de la file et ils sont supprimés de l'avant de la file. Le début et la fin d'une file peuvent être inspectés. L’utilisation de la classe queue s’explique par cette limitation qui fait que seuls les éléments à l’avant et à l’arrière sont accessibles de cette façon.

- La classe priority_queue trie ses éléments pour que l’élément le plus grand soit toujours en haut. Elle prend en charge l'insertion d'un élément, et l'inspection et la suppression de l'élément du haut. Une bonne analogie à avoir à l'esprit est celle de personnes faisant la file, classées selon leur âge, leur taille ou un autre critère.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[priority_queue](#priority_queue)|Construit un `priority_queue` qui est vide ou qui est une copie d’une plage d’un objet conteneur de base ou d’un autre `priority_queue`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[container_type](#container_type)|Type qui fournit le conteneur de base à adapter par un objet `priority_queue`.|
|[size_type](#size_type)|Type entier non signé qui peut représenter le nombre d'éléments dans un `priority_queue`.|
|[value_type](#value_type)|Type qui représente le type d'objet stocké en tant qu'élément dans un objet `priority_queue`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[empty](#empty)|Vérifie si l'objet `priority_queue` est vide.|
|[pop](#pop)|Supprime l’élément le plus grand en haut du `priority_queue`.|
|[push](#push)|Ajoute un élément à la file d’attente à priorité en fonction de la priorité de l’élément définie par l’opérateur <.|
|[size](#size)|Retourne le nombre d'éléments d'un `priority_queue`.|
|[top](#top)|Retourne une référence const à l’élément le plus grand en haut du `priority_queue`.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<queue>

**Espace de noms :** std

## <a name="container_type"></a>  priority_queue::container_type

Type qui fournit le conteneur de base à adapter.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Container`. La classe de conteneur de séquence `deque` et la classe par défaut `vector` de la bibliothèque standard C++ remplissent les conditions pour être utilisées comme conteneur de base d’un objet priority_queue. Les types définis par l’utilisateur peuvent également être utilisés s’ils remplissent les conditions.

Pour plus d’informations sur `Container`, consultez la section Notes de la rubrique [priority_queue, classe](../standard-library/priority-queue-class.md).

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `container_type`, consultez l’exemple [priority_queue](#priority_queue).

## <a name="empty"></a>  priority_queue::empty

Teste si un objet priority_queue est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si l’objet priority_queue est vide. **false** s’il n’est pas vide.

### <a name="example"></a>Exemple

```cpp
// pqueue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue <int> q1, s2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The priority_queue q1 is empty." << endl;
   else
      cout << "The priority_queue q1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The priority_queue s2 is empty." << endl;
   else
      cout << "The priority_queue s2 is not empty." << endl;
}
```

```Output
The priority_queue q1 is not empty.
The priority_queue s2 is empty.
```

## <a name="pop"></a>  priority_queue::pop

Supprime l’élément le plus grand en haut du priority_queue.

```cpp
void pop();
```

### <a name="remarks"></a>Notes

La file d'attente priority_queue ne doit pas être vide pour appliquer la fonction membre. Le plus grand élément du conteneur se trouve toujours en haut du priority_queue.

### <a name="example"></a>Exemple

```cpp
// pqueue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   priority_queue <int>::size_type i, iii;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;

   q1.pop( );

   iii = q1.size( );
   cout << "After a pop, the priority_queue length is "
        << iii << "." << endl;

   const int& iv = q1.top( );
   cout << "After a pop, the element at the top of the "
        << "priority_queue is " << iv << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
After a pop, the priority_queue length is 2.
After a pop, the element at the top of the priority_queue is 20.
```

## <a name="priority_queue"></a>  priority_queue::priority_queue

Construit un priority_queue qui est vide ou qui est une copie d’une plage d’un objet conteneur de base ou d’un autre priority_queue.

```cpp
priority_queue();

explicit priority_queue(const Traits&_comp);

priority_queue(const Traits&_comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits&_comp);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits&_comp, const container_type& _Cont);
```

### <a name="parameters"></a>Paramètres

*_ comp* la fonction de comparaison de type **constTraits** utilisée pour trier les éléments dans le priority_queue, qui utilise par défaut pour comparer la fonction du conteneur de base.

`_Cont` Le conteneur de base dont le priority_queue construit est doit être une copie.

`right` Le priority_queue dont le jeu construit doit être une copie.

`first` La position du premier élément dans la plage d’éléments à copier.

`last` Position du premier élément au-delà de la plage d’éléments à copier.

### <a name="remarks"></a>Notes

Chacun des trois premiers constructeurs spécifie un priority_queue initial vide. Le deuxième constructeur spécifie aussi le type de fonction de comparaison ( `comp`) à utiliser pour classer les éléments. Le troisième constructeur spécifie explicitement le `container_type` ( `_Cont`) à utiliser. Le mot clé **explicit** supprime certains genres de conversions de type automatiques.

Le quatrième constructeur spécifie une copie du priority_queue `right`.

Les trois dernières constructeurs copient la plage [* tout d’abord, dernier *) d’un conteneur et les valeurs utilisées pour initialiser un priority_queue en augmentant le caractère explicite en spécifiant le type de fonction de comparaison de la classe **caractéristiques** et `container_type`.

### <a name="example"></a>Exemple

```cpp
// pqueue_ctor.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <deque>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function declares priority_queue
   // with a default vector base container
   priority_queue <int> q1;
   cout << "q1 = ( ";
   while ( !q1.empty( ) )
   {
      cout << q1.top( ) << " ";
      q1.pop( );
   }
   cout << ")" << endl;

   // Explicitly declares a priority_queue with nondefault
   // deque base container
   priority_queue <int, deque <int> > q2;
   q2.push( 5 );
   q2.push( 15 );
   q2.push( 10 );
   cout << "q2 = ( ";
   while ( !q2.empty( ) )
   {
      cout << q2.top( ) << " ";
      q2.pop( );
   }
   cout << ")" << endl;

   // This method of printing out the elements of a priority_queue
   // removes the elements from the priority queue, leaving it empty
   cout << "After printing, q2 has " << q2.size( ) << " elements." << endl;

   // The third member function declares a priority_queue
   // with a vector base container and specifies that the comparison
   // function greater is to be used for ordering elements
   priority_queue <int, vector<int>, greater<int> > q3;
   q3.push( 2 );
   q3.push( 1 );
   q3.push( 3 );
   cout << "q3 = ( ";
   while ( !q3.empty( ) )
   {
      cout << q3.top( ) << " ";
      q3.pop( );
   }
   cout << ")" << endl;

   // The fourth member function declares a priority_queue and
   // initializes it with elements copied from another container:
   // first, inserting elements into q1, then copying q1 elements into q4
   q1.push( 100 );
   q1.push( 200 );
   priority_queue <int> q4( q1 );
   cout << "q4 = ( ";
   while ( !q4.empty( ) )
   {
      cout << q4.top( ) << " ";
      q4.pop( );
   }
   cout << ")" << endl;

   // Creates an auxiliary vector object v5 to be used to initialize q5
   vector <int> v5;
   vector <int>::iterator v5_Iter;
   v5.push_back( 10 );
   v5.push_back( 30 );
   v5.push_back( 20 );
   cout << "v5 = ( " ;
   for ( v5_Iter = v5.begin( ) ; v5_Iter != v5.end( ) ; v5_Iter++ )
      cout << *v5_Iter << " ";
   cout << ")" << endl;

   // The fifth member function declares and
   // initializes a priority_queue q5 by copying the
   // range v5[ first,  last) from vector v5
   priority_queue <int> q5( v5.begin( ), v5.begin( ) + 2 );
   cout << "q5 = ( ";
   while ( !q5.empty( ) )
   {
      cout << q5.top( ) << " ";
      q5.pop( );
   }
   cout << ")" << endl;

   // The sixth member function declares a priority_queue q6
   // with a comparison function greater and initializes q6
   // by copying the range v5[ first,  last) from vector v5
   priority_queue <int, vector<int>, greater<int> >
      q6( v5.begin( ), v5.begin( ) + 2 );
   cout << "q6 = ( ";
   while ( !q6.empty( ) )
   {
      cout << q6.top( ) << " ";
      q6.pop( );
   }
   cout << ")" << endl;
}
```

## <a name="push"></a>  priority_queue::push

Ajoute un élément à la file d’attente à priorité en fonction de la priorité de l’élément définie par l’opérateur <.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Paramètres

`val` L’élément est ajouté en haut de la priority_queue.

### <a name="remarks"></a>Notes

Le haut du priority_queue est la position occupée par l’élément le plus grand dans le conteneur.

### <a name="example"></a>Exemple

```cpp
// pqueue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="size"></a>  priority_queue::size

Retourne le nombre d’éléments figurant dans le priority_queue.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur actuelle du priority_queue.

### <a name="example"></a>Exemple

```cpp
// pqueue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, q2;
   priority_queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The priority_queue length is now " << i << "." << endl;
}
```

```Output
The priority_queue length is 1.
The priority_queue length is now 2.
```

## <a name="size_type"></a>  priority_queue::size_type

Type entier non signé qui peut représenter le nombre d’éléments dans un priority_queue.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du `size_type` pour le conteneur de base adapté par le priority_queue.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `size_type`, consultez l’exemple [size](#size).

## <a name="top"></a>  priority_queue::top

Retourne une référence à l'élément le plus grand en haut de la file d'attente priority_queue.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>Valeur de retour

Référence à l’élément le plus grand dans le priority_queue, tel que déterminé par la fonction **Traits**.

### <a name="remarks"></a>Notes

La file d'attente priority_queue ne doit pas être vide pour appliquer la fonction membre.

### <a name="example"></a>Exemple

```cpp
// pqueue_top.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="value_type"></a>  priority_queue::value_type

Type qui représente le type de l’objet stocké comme élément dans un priority_queue.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du `value_type` pour le conteneur de base adapté par le priority_queue.

### <a name="example"></a>Exemple

```cpp
// pqueue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   priority_queue<int> q1;
   q1.push( AnInt );
   cout << "The element at the top of the priority_queue is "
        << q1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the priority_queue is 69.
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
