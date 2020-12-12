---
description: 'En savoir plus sur : priority_queue (STL/CLR)'
title: priority_queue (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::priority_queue
- cliext::priority_queue::assign
- cliext::priority_queue::const_reference
- cliext::priority_queue::container_type
- cliext::priority_queue::difference_type
- cliext::priority_queue::empty
- cliext::priority_queue::generic_container
- cliext::priority_queue::generic_value
- cliext::priority_queue::get_container
- cliext::priority_queue::operator=
- cliext::priority_queue::pop
- cliext::priority_queue::priority_queue
- cliext::priority_queue::push
- cliext::priority_queue::reference
- cliext::priority_queue::size
- cliext::priority_queue::size_type
- cliext::priority_queue::to_array
- cliext::priority_queue::top
- cliext::priority_queue::top_item
- cliext::priority_queue::value_comp
- cliext::priority_queue::value_compare
- cliext::priority_queue::value_type
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
- assign member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- priority_queue member [STL/CLR]
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
ms.openlocfilehash: 666efbc634ae962836fce4fa12ca762ab7085d92
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282495"
---
# <a name="priority_queue-stlclr"></a>priority_queue (STL/CLR)

La classe de modèle décrit un objet qui contrôle une séquence ordonnée d’éléments de longueur variable ayant un accès limité. Vous utilisez l’adaptateur `priority_queue` de conteneur pour gérer un conteneur sous-jacent en tant que file d’attente de priorité.

Dans la description ci-dessous, `GValue` est le même que la *valeur* , sauf si ce dernier est un type REF, auquel cas il s’agit de `Value^` . De même, `GContainer` est le même que le *conteneur* , sauf si ce dernier est un type REF, auquel cas il s’agit de `Container^` .

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    ref class priority_queue
        System::ICloneable,
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>Paramètres

*Valeur*<br/>
Type d'un élément dans la séquence contrôlée.

*Conteneur*<br/>
Type du conteneur sous-jacent.

## <a name="requirements"></a>Spécifications

**En-tête :**\<cliext/queue>

**Espace de noms :** cliext

## <a name="declarations"></a>Déclarations

|Définition de type|Description|
|---------------------|-----------------|
|[priority_queue::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|
|[priority_queue::container_type (STL/CLR)](#container_type)|Type du conteneur sous-jacent.|
|[priority_queue::difference_type (STL/CLR)](#difference_type)|Type d'une distance signée entre deux éléments.|
|[priority_queue::generic_container (STL/CLR)](#generic_container)|Type de l’interface générique pour l’adaptateur de conteneur.|
|[priority_queue::generic_value (STL/CLR)](#generic_value)|Type d’un élément pour l’interface générique de l’adaptateur de conteneur.|
|[priority_queue::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|
|[priority_queue::size_type (STL/CLR)](#size_type)|Type d'une distance signée entre deux éléments.|
|[priority_queue::value_compare (STL/CLR)](#value_compare)|Délégué de classement pour deux éléments.|
|[priority_queue::value_type (STL/CLR)](#value_type)|Type d’un élément.|

|Fonction membre|Description|
|---------------------|-----------------|
|[priority_queue::assign (STL/CLR)](#assign)|Remplace tous les éléments.|
|[priority_queue::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|
|[priority_queue::get_container (STL/CLR)](#get_container)|Accède au conteneur sous-jacent.|
|[priority_queue::pop (STL/CLR)](#pop)|Supprime l’élément hghest-Priority.|
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|Construit un objet conteneur.|
|[priority_queue::push (STL/CLR)](#push)|Ajoute un nouvel élément.|
|[priority_queue::size (STL/CLR)](#size)|Compte le nombre d'éléments.|
|[priority_queue::top (STL/CLR)](#top)|Accède à l’élément dont la priorité est la plus élevée.|
|[priority_queue::to_array (STL/CLR)](#to_array)|Copie la séquence contrôlée dans un nouveau tableau.|
|[priority_queue::value_comp (STL/CLR)](#value_comp)|Copie le délégué de classement pour deux éléments.|

|Propriété|Description|
|--------------|-----------------|
|[priority_queue::top_item (STL/CLR)](#top_item)|Accède à l’élément dont la priorité est la plus élevée.|

|Opérateur|Description|
|--------------|-----------------|
|[priority_queue::operator= (STL/CLR)](#op_as)|Remplace la séquence contrôlée.|

## <a name="interfaces"></a>Interfaces

|Interface|Description|
|---------------|-----------------|
|<xref:System.ICloneable>|Dupliquer un objet.|
|IPriorityQueue\<Value, Container>|Gérer l’adaptateur de conteneur générique.|

## <a name="remarks"></a>Notes

L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un conteneur sous-jacent, de type `Container` , qui stocke des `Value` éléments et se développe à la demande. Elle conserve la séquence ordonnée comme un segment de mémoire, avec l’élément dont la priorité est la plus élevée (l’élément supérieur) facilement accessible et amovible. L’objet limite l’accès en envoyant de nouveaux éléments et en dépilant simplement l’élément dont la priorité est la plus élevée, en implémentant une file d’attente de priorité.

L’objet trie la séquence qu’il contrôle en appelant un objet délégué stocké de type [priority_queue :: value_compare (STL/CLR)](#value_compare). Vous pouvez spécifier l’objet délégué stocké quand vous construisez le priority_queue ; Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la comparaison `operator<(value_type, value_type)` . Vous accédez à cet objet stocké en appelant la fonction membre [priority_queue :: value_comp (STL/CLR)](#value_comp) `()` .

Un tel objet délégué doit imposer un classement faible strict sur les valeurs de type [priority_queue :: Value_type (STL/CLR)](#value_type). Cela signifie, pour deux clés `X` et `Y` :

`value_comp()(X, Y)` retourne le même résultat booléen pour chaque appel.

Si `value_comp()(X, Y)` a la valeur true, `value_comp()(Y, X)` doit avoir la valeur false.

Si `value_comp()(X, Y)` a la valeur true, `X` est dit être trié avant `Y` .

Si `!value_comp()(X, Y) && !value_comp()(Y, X)` a la valeur true, `X` et `Y` sont considérés comme ayant un ordre équivalent.

Pour tout élément `X` qui précède `Y` dans la séquence contrôlée, `key_comp()(Y, X)` est false. (Pour l’objet délégué par défaut, les clés ne diminuent jamais la valeur.)

L’élément dont la priorité est la plus élevée est donc l’un des éléments qui n’est pas ordonné avant tout autre élément.

Étant donné que le conteneur sous-jacent conserve les éléments ordonnés comme un segment de mémoire :

Le conteneur doit prendre en charge les itérateurs à accès aléatoire.

Les éléments avec un classement équivalent peuvent être dépilés dans un ordre différent de celui dans lequel ils ont été envoyés. (Le classement n’est pas stable.)

Par conséquent, les candidats pour le conteneur sous-jacent incluent [deque (STL/CLR)](../dotnet/deque-stl-clr.md) et [Vector (STL/CLR)](../dotnet/vector-stl-clr.md).

## <a name="members"></a>Membres

## <a name="priority_queueassign-stlclr"></a><a name="assign"></a> priority_queue :: assign (STL/CLR)

Remplace tous les éléments.

### <a name="syntax"></a>Syntaxe

```cpp
void assign(priority_queue<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Adaptateur de conteneur à insérer.

### <a name="remarks"></a>Notes

La fonction membre est assignée `right.get_container()` au conteneur sous-jacent. Vous l’utilisez pour modifier la totalité du contenu de la file d’attente.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_assign.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign a repetition of values
    Mypriority_queue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queueconst_reference-stlclr"></a><a name="const_reference"></a> priority_queue :: const_reference (STL/CLR)

Type d'une référence constante à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence constante à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_const_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mypriority_queue::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="priority_queuecontainer_type-stlclr"></a><a name="container_type"></a> priority_queue :: container_type (STL/CLR)

Type du conteneur sous-jacent.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Container`.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_container_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c" using container_type
    Mypriority_queue::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuedifference_type-stlclr"></a><a name="difference_type"></a> priority_queue ::d ifference_type (STL/CLR)

Types d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments éventuellement négatifs.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_difference_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute negative difference
    Mypriority_queue::difference_type diff = c1.size();
    c1.push(L'd');
    c1.push(L'e');
    diff -= c1.size();
    System::Console::WriteLine("pushing 2 = {0}", diff);

    // compute positive difference
    diff = c1.size();
    c1.pop();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("popping 3 = {0}", diff);
    return (0);
    }
```

```Output
c a b
pushing 2 = -2
popping 3 = 3
```

## <a name="priority_queueempty-stlclr"></a><a name="empty"></a> priority_queue :: Empty (STL/CLR)

Vérifie l'absence d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur true pour une séquence contrôlée vide. Elle équivaut à [priority_queue :: Size (STL/CLR)](#size) `() == 0` . Vous l’utilisez pour tester si le priority_queue est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_empty.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.pop();
    c1.pop();
    c1.pop();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
c a b
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="priority_queuegeneric_container-stlclr"></a><a name="generic_container"></a> priority_queue :: generic_container (STL/CLR)

Type de l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>
    generic_container;
```

### <a name="remarks"></a>Notes

Le type décrit l’interface générique pour cette classe d’adaptateur de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_generic_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push(L'e');
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
d c b a
e d b a c
```

## <a name="priority_queuegeneric_value-stlclr"></a><a name="generic_value"></a> priority_queue :: generic_value (STL/CLR)

Type d’un élément à utiliser avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stocké à utiliser avec l’interface générique pour cette classe de conteneur de modèle. ( `GValue` a `value_type` la valeur ou `value_type^` si `value_type` est un type Ref.)

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_generic_value.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get interface to container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display in priority order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mypriority_queue::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
c b a
```

## <a name="priority_queueget_container-stlclr"></a><a name="get_container"></a> priority_queue :: get_container (STL/CLR)

Accède au conteneur sous-jacent.

### <a name="syntax"></a>Syntaxe

```cpp
container_type get_container();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le conteneur sous-jacent. Vous l’utilisez pour ignorer les restrictions imposées par le wrapper de conteneur.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_get_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queueoperator-stlclr"></a><a name="op_as"></a> priority_queue :: Operator = (STL/CLR)

Remplace la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Adaptateur de conteneur à copier.

### <a name="remarks"></a>Notes

L’opérateur membre copie *directement* vers l’objet, puis retourne **`*this`** . Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans *Right*.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_operator_as.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mypriority_queue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queuepop-stlclr"></a><a name="pop"></a> priority_queue ::p op (STL/CLR)

Supprime l’élément proirity le plus élevé.

### <a name="syntax"></a>Syntaxe

```cpp
void pop();
```

### <a name="remarks"></a>Notes

La fonction membre supprime l’élément de priorité la plus élevée de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour raccourcir la file d’attente d’un élément à l’arrière.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_pop.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop();
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
b a
```

## <a name="priority_queuepriority_queue-stlclr"></a><a name="priority_queue"></a> priority_queue ::p riority_queue (STL/CLR)

Construit un objet adaptateur de conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
priority_queue();
priority_queue(priority_queue<Value, Container> right);
priority_queue(priority_queue<Value, Container> right);
explicit priority_queue(value_compare^ pred);
priority_queue(value_compare^ pred, container_type% cont);
template<typename InIt>
    priority_queue(InIt first, InIt last);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred, container_type% cont);
```

#### <a name="parameters"></a>Paramètres

*livraison continue*<br/>
Conteneur à copier.

*first*<br/>
Début de la plage à insérer.

*last*<br/>
Fin de la plage à insérer.

*prédit*<br/>
Prédicat de classement pour la séquence contrôlée.

*Oui*<br/>
Objet ou plage à insérer.

### <a name="remarks"></a>Notes

Le constructeur :

`priority_queue();`

crée un conteneur encapsulé vide, avec le prédicat de classement par défaut. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide, avec le prédicat de classement par défaut.

Le constructeur :

`priority_queue(priority_queue<Value, Container>% right);`

crée un conteneur encapsulé qui est une copie de `right.get_container()` , avec le prédicat de classement `right.value_comp()` . Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par le *droit* de l’objet de file d’attente, avec le même prédicat de classement.

Le constructeur :

`priority_queue(priority_queue<Value, Container>^ right);`

crée un conteneur encapsulé qui est une copie de `right->get_container()` , avec le prédicat de classement `right->value_comp()` . Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de file d’attente `*right` , avec le même prédicat de classement.

Le constructeur :

`explicit priority_queue(value_compare^ pred);`

crée un conteneur encapsulé vide, avec le prédicat de classement *prédit*. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide, avec le prédicat de tri spécifié.

Le constructeur :

`priority_queue(value_compare^ pred, container_type cont);`

crée un conteneur encapsulé vide, avec le prédicat de classement *prédit*, puis exécute un push de tous les *éléments de l'* élément que vous utilisez pour spécifier une séquence contrôlée initiale à partir d’un conteneur existant, avec le prédicat de tri spécifié.

Le constructeur :

`template<typename InIt> priority_queue(InIt first, InIt last);`

crée un conteneur encapsulé vide, avec le prédicat de classement par défaut, puis exécute un push de la séquence [ `first` , `last` ). Vous l’utilisez pour spécifier une séquence contrôlée initiale à partir d’un eqeuence spécifié, avec le prédicat de tri spécifié.

Le constructeur :

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`

crée un conteneur encapsulé vide, avec le prédicat de classement *prédit*, puis exécute un push de la séquence [ `first` , `last` ). Vous l’utilisez pour spécifier une séquence contrôlée initiale à partir d’un seqeuence spécifié, avec le prédicat de tri spécifié.

Le constructeur :

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`

crée un conteneur encapsulé vide, avec le prédicat de classement *prédit*, puis exécute un push de tous les éléments de *suite* plus la séquence [ `first` , `last` ). Vous l’utilisez pour spécifier une séquence contrôlée initiale à partir d’un conteneur existant et d’un seqeuence spécifié, avec le prédicat de tri spécifié.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_construct.cpp
// compile with: /clr
#include <cliext/queue>
#include <cliext/deque>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
typedef cliext::deque<wchar_t> Mydeque;
int main()
    {
// construct an empty container
    Mypriority_queue c1;
    Mypriority_queue::container_type^ wc1 = c1.get_container();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    for each (wchar_t elem in wc1)
        c2.push(elem);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule by copying an underlying container
    Mypriority_queue c2x =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
   for each (wchar_t elem in c2x.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mypriority_queue c3(wc1->begin(), wc1->end());
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mypriority_queue c4(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>());
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range, another container, and an ordering rule
    Mypriority_queue c5(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c5.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mypriority_queue c6(c3);
    for each (wchar_t elem in c6.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mypriority_queue c7(%c3);
    for each (wchar_t elem in c7.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule, by copying an underlying container
    Mypriority_queue c8 =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c8.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
c a b
size() = 0
a c b
a c b
c a b
a c b
a a b c c b
c a b
c a b
a c b
```

## <a name="priority_queuepush-stlclr"></a><a name="push"></a> priority_queue ::p par émission (STL/CLR)

Ajoute un nouvel élément.

### <a name="syntax"></a>Syntaxe

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Notes

La fonction membre insère un élément avec une valeur `val` dans la séquence contrôlée et réorganise la séquence contrôlée pour maintenir la discipline du tas. Vous l’utilisez pour ajouter un autre élément à la file d’attente.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_push.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuereference-stlclr"></a><a name="reference"></a> priority_queue :: Reference (STL/CLR)

Type d'une référence à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify top of priority_queue and redisplay
    Mypriority_queue::reference ref = c1.top();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
x a b
```

## <a name="priority_queuesize-stlclr"></a><a name="size"></a> priority_queue :: Size (STL/CLR)

Compte le nombre d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence contrôlée. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si vous vous intéressez uniquement si la séquence a une taille différente de zéro, consultez [priority_queue :: Empty (STL/CLR)](#empty) `()` .

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_size.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // pop an item and reinspect
    c1.pop();
    System::Console::WriteLine("size() = {0} after popping", c1.size());

    // add two elements and reinspect
    c1.push(L'a');
    c1.push(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
c a b
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="priority_queuesize_type-stlclr"></a><a name="size_type"></a> priority_queue :: size_type (STL/CLR)

Type d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments non négatifs.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_size_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mypriority_queue::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
c a b
size difference = 2
```

## <a name="priority_queueto_array-stlclr"></a><a name="to_array"></a> priority_queue :: to_array (STL/CLR)

Copie la séquence contrôlée dans un nouveau tableau.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un tableau contenant la séquence contrôlée. Vous l’utilisez pour obtenir une copie de la séquence contrôlée sous forme de tableau.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_to_array.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
d c b a
c a b
```

## <a name="priority_queuetop-stlclr"></a><a name="top"></a> priority_queue :: Top (STL/CLR)

Accède à l’élément dont la priorité est la plus élevée.

### <a name="syntax"></a>Syntaxe

```cpp
reference top();
```

### <a name="remarks"></a>Notes

La fonction membre retourne une référence à l’élément supérieur (priorité la plus élevée) de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour accéder à l’élément dont la priorité est la plus élevée, lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_top.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top() = {0}", c1.top());

    // alter last item and reinspect
    c1.top() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

## <a name="priority_queuetop_item-stlclr"></a><a name="top_item"></a> priority_queue :: top_item (STL/CLR)

Accède à l’élément dont la priorité est la plus élevée.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Notes

La propriété accède à l’élément supérieur (priorité la plus élevée) de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour lire ou écrire l’élément dont la priorité est la plus élevée, si vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_top_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top_item = {0}", c1.top_item);

    // alter last item and reinspect
    c1.top_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
top_item = c
x a b
```

## <a name="priority_queuevalue_comp-stlclr"></a><a name="value_comp"></a> priority_queue :: value_comp (STL/CLR)

Copie le délégué de classement pour deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le délégué de classement utilisé pour ordonner la séquence contrôlée. Vous l'utilisez pour comparer deux valeurs.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_value_comp.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="priority_queuevalue_compare-stlclr"></a><a name="value_compare"></a> priority_queue :: value_compare (STL/CLR)

Délégué de classement pour deux valeurs.

### <a name="syntax"></a>Syntaxe

```cpp
binary_delegate<value_type, value_type, int> value_compare;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du délégué qui détermine si le premier argument est ordonné avant le second.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_value_compare.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="priority_queuevalue_type-stlclr"></a><a name="value_type"></a> priority_queue :: value_type (STL/CLR)

Type d’un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la *valeur* de paramètre de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_priority_queue_value_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mypriority_queue::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```
