---
description: 'En savoir plus sur : file d’attente (STL/CLR)'
title: queue (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::queue
- cliext::queue::assign
- cliext::queue::back
- cliext::queue::back_item
- cliext::queue::const_reference
- cliext::queue::container_type
- cliext::queue::difference_type
- cliext::queue::empty
- cliext::queue::front
- cliext::queue::front_item
- cliext::queue::generic_container
- cliext::queue::generic_value
- cliext::queue::get_container
- cliext::queue::operator=
- cliext::queue::pop
- cliext::queue::push
- cliext::queue::queue
- cliext::queue::reference
- cliext::queue::size
- cliext::queue::size_type
- cliext::queue::to_array
- cliext::queue::value_type
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- push member [STL/CLR]
- queue member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
ms.openlocfilehash: 1cbe30dff567c81840f2b78498b04648954399dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245874"
---
# <a name="queue-stlclr"></a>queue (STL/CLR)

La classe de modèle décrit un objet qui contrôle une séquence de longueur variable d’éléments ayant un premier accès premier sorti. Vous utilisez l’adaptateur `queue` de conteneur pour gérer un conteneur sous-jacent en tant que file d’attente.

Dans la description ci-dessous, `GValue` est le même que la *valeur* , sauf si ce dernier est un type REF, auquel cas il s’agit de `Value^` . De même, `GContainer` est le même que le *conteneur* , sauf si ce dernier est un type REF, auquel cas il s’agit de `Container^` .

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    ref class queue
        :   public
        System::ICloneable,
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>
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
|[queue::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|
|[queue::container_type (STL/CLR)](#container_type)|Type du conteneur sous-jacent.|
|[queue::difference_type (STL/CLR)](#difference_type)|Type d'une distance signée entre deux éléments.|
|[queue::generic_container (STL/CLR)](#generic_container)|Type de l’interface générique pour l’adaptateur de conteneur.|
|[queue::generic_value (STL/CLR)](#generic_value)|Type d’un élément pour l’interface générique de l’adaptateur de conteneur.|
|[queue::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|
|[queue::size_type (STL/CLR)](#size_type)|Type d'une distance signée entre deux éléments.|
|[queue::value_type (STL/CLR)](#value_type)|Type d’un élément.|

|Fonction membre|Description|
|---------------------|-----------------|
|[queue::assign (STL/CLR)](#assign)|Remplace tous les éléments.|
|[queue::back (STL/CLR)](#back)|Accède au dernier élément.|
|[queue::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|
|[queue::front (STL/CLR)](#front)|Accède au premier élément.|
|[queue::get_container (STL/CLR)](#get_container)|Accède au conteneur sous-jacent.|
|[queue::pop (STL/CLR)](#pop)|Supprime le premier élément.|
|[queue::push (STL/CLR)](#push)|Ajoute un nouveau dernier élément.|
|[queue::queue (STL/CLR)](#queue)|Construit un objet conteneur.|
|[queue::size (STL/CLR)](#size)|Compte le nombre d'éléments.|
|[queue::to_array (STL/CLR)](#to_array)|Copie la séquence contrôlée dans un nouveau tableau.|

|Propriété|Description|
|--------------|-----------------|
|[queue::back_item (STL/CLR)](#back_item)|Accède au dernier élément.|
|[queue::front_item (STL/CLR)](#front_item)|Accède au premier élément.|

|Opérateur|Description|
|--------------|-----------------|
|[queue::operator= (STL/CLR)](#op_as)|Remplace la séquence contrôlée.|
|[Operator ! = (file d’attente) (STL/CLR)](#op_neq)|Détermine si un `queue` objet n’est pas égal à un autre `queue` objet.|
|[< d’opérateur (file d’attente) (STL/CLR)](#op_lt)|Détermine si un `queue` objet est inférieur à un autre `queue` objet.|
|[opérateur<= (file d’attente) (STL/CLR)](#op_lteq)|Détermine si un `queue` objet est inférieur ou égal à un autre `queue` objet.|
|[opérateur = = (file d’attente) (STL/CLR)](#op_eq)|Détermine si un `queue` objet est égal à un autre `queue` objet.|
|[> d’opérateur (file d’attente) (STL/CLR)](#op_gt)|Détermine si un `queue` objet est supérieur à un autre `queue` objet.|
|[operator>= (queue) (STL/CLR)](#op_gteq)|Détermine si un `queue` objet est supérieur ou égal à un autre `queue` objet.|

## <a name="interfaces"></a>Interfaces

|Interface|Description|
|---------------|-----------------|
|<xref:System.ICloneable>|Dupliquer un objet.|
|IQueue\<Value, Container>|Gérer l’adaptateur de conteneur générique.|

## <a name="remarks"></a>Notes

L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un conteneur sous-jacent, de type `Container` , qui stocke des `Value` éléments et se développe à la demande. L’objet restreint l’accès au simple push du premier élément et en dépilant le dernier élément, en implémentant une file d’attente First-in First-Out (également appelée file d’attente FIFO ou simplement une file d’attente).

## <a name="members"></a>Membres

## <a name="queueassign-stlclr"></a><a name="assign"></a> queue :: assign (STL/CLR)

Remplace tous les éléments.

### <a name="syntax"></a>Syntaxe

```cpp
void assign(queue<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Adaptateur de conteneur à insérer.

### <a name="remarks"></a>Notes

La fonction membre est assignée `right.get_container()` au conteneur sous-jacent. Vous l’utilisez pour modifier la totalité du contenu de la file d’attente.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_assign.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign a repetition of values
    Myqueue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="queueback-stlclr"></a><a name="back"></a> queue :: Back (STL/CLR)

Accède au dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
reference back();
```

### <a name="remarks"></a>Notes

La fonction membre retourne une référence au dernier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour accéder au dernier élément, lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_back.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

// alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="queueback_item-stlclr"></a><a name="back_item"></a> queue :: back_item (STL/CLR)

Accède au dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Notes

La propriété accède au dernier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour lire ou écrire le dernier élément, lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_back_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

// alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="queueconst_reference-stlclr"></a><a name="const_reference"></a> queue :: const_reference (STL/CLR)

Type d'une référence constante à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence constante à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_const_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Myqueue::const_reference cref = c1.front();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="queuecontainer_type-stlclr"></a><a name="container_type"></a> queue :: container_type (STL/CLR)

Type du conteneur sous-jacent.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Container`.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_container_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Myqueue::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="queuedifference_type-stlclr"></a><a name="difference_type"></a> file d’attente ::d ifference_type (STL/CLR)

Types d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments éventuellement négatifs.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_difference_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute negative difference
    Myqueue::difference_type diff = c1.size();
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
a b c
pushing 2 = -2
popping 3 = 3
```

## <a name="queueempty-stlclr"></a><a name="empty"></a> queue :: Empty (STL/CLR)

Vérifie l'absence d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur true pour une séquence contrôlée vide. Elle est équivalente à [queue :: Size (STL/CLR)](#size) `() == 0` . Vous l’utilisez pour tester si la file d’attente est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_empty.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="queuefront-stlclr"></a><a name="front"></a> queue :: Front (STL/CLR)

Accède au premier élément.

### <a name="syntax"></a>Syntaxe

```cpp
reference front();
```

### <a name="remarks"></a>Notes

La fonction membre retourne une référence au premier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour accéder au premier élément, lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_front.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

// alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

## <a name="queuefront_item-stlclr"></a><a name="front_item"></a> queue :: front_item (STL/CLR)

Accède au premier élément.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Notes

La propriété accède au premier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour lire ou écrire le premier élément, lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_front_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

// alter last item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

## <a name="queuegeneric_container-stlclr"></a><a name="generic_container"></a> queue :: generic_container (STL/CLR)

Type de l’interface générique pour l’adaptateur de conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::IQueue<Value>
    generic_container;
```

### <a name="remarks"></a>Notes

Le type décrit l’interface générique pour cette classe d’adaptateur de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_generic_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myqueue::generic_container^ gc1 = %c1;
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
a b c
a b c
a b c d
a b c d e
```

## <a name="queuegeneric_value-stlclr"></a><a name="generic_value"></a> queue :: generic_value (STL/CLR)

Type d’un élément à utiliser avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stocké à utiliser avec l’interface générique pour cette classe de conteneur de modèle. ( `GValue` a `value_type` la valeur ou `value_type^` si `value_type` est un type Ref.)

### <a name="example"></a>Exemple

```cpp
// cliext_queue_generic_value.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Myqueue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display in order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Myqueue::generic_value elem = gc1->front();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c
```

## <a name="queueget_container-stlclr"></a><a name="get_container"></a> queue :: get_container (STL/CLR)

Accède au conteneur sous-jacent.

### <a name="syntax"></a>Syntaxe

```cpp
container_type^ get_container();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le conteneur sous-jacent. Vous l’utilisez pour ignorer les restrictions imposées par le wrapper de conteneur.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_get_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
```

## <a name="queueoperator-stlclr"></a><a name="op_as"></a> queue :: Operator = (STL/CLR)

Remplace la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
queue <Value, Container>% operator=(queue <Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Adaptateur de conteneur à copier.

### <a name="remarks"></a>Notes

L’opérateur membre copie *directement* vers l’objet, puis retourne **`*this`** . Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans *Right*.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_operator_as.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="queuepop-stlclr"></a><a name="pop"></a> file d’attente ::p op (STL/CLR)

Supprime le dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
void pop();
```

### <a name="remarks"></a>Notes

La fonction membre supprime le dernier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour raccourcir la file d’attente d’un élément à l’arrière.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_pop.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
b c
```

## <a name="queuepush-stlclr"></a><a name="push"></a> file d’attente ::p par émission (STL/CLR)

Ajoute un nouveau dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Notes

La fonction membre ajoute un élément avec une valeur `val` à la fin de la file d’attente. Vous l’utilisez pour ajouter un élément à la file d’attente.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_push.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
```

## <a name="queuequeue-stlclr"></a><a name="queue"></a> queue :: queue (STL/CLR)

Construit un objet adaptateur de conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
queue();
queue(queue<Value, Container>% right);
queue(queue<Value, Container>^ right);
explicit queue(container_type% wrapped);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Objet à copier.

*encapsulée*<br/>
Conteneur encapsulé à utiliser.

### <a name="remarks"></a>Notes

Le constructeur :

`queue();`

crée un conteneur encapsulé vide. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide.

Le constructeur :

`queue(queue<Value, Container>% right);`

crée un conteneur encapsulé qui est une copie de `right.get_container()` . Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par le *droit* de l’objet de file d’attente.

Le constructeur :

`queue(queue<Value, Container>^ right);`

crée un conteneur encapsulé qui est une copie de `right->get_container()` . Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de file d’attente `*right` .

Le constructeur :

`explicit queue(container_type wrapped);`

utilise le conteneur existant *encapsulé* comme conteneur encapsulé. Vous l’utilisez pour construire une file d’attente à partir d’un conteneur existant.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_construct.cpp
// compile with: /clr
#include <cliext/queue>
#include <cliext/list>

typedef cliext::queue<wchar_t> Myqueue;
typedef cliext::list<wchar_t> Mylist;
typedef cliext::queue<wchar_t, Mylist> Myqueue_list;
int main()
    {
// construct an empty container
    Myqueue c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct from an underlying container
    Mylist v2(5, L'x');
    Myqueue_list c2(v2);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Myqueue_list c3(c2);
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container through handle
    Myqueue_list c4(%c2);
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
x x x x x
x x x x x
x x x x x
```

## <a name="queuereference-stlclr"></a><a name="reference"></a> queue :: Reference (STL/CLR)

Type d'une référence à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify back of queue and redisplay
    Myqueue::reference ref = c1.back();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b x
```

## <a name="queuesize-stlclr"></a><a name="size"></a> queue :: Size (STL/CLR)

Compte le nombre d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence contrôlée. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si vous vous intéressez uniquement si la séquence a une taille différente de zéro, consultez [queue :: Empty (STL/CLR)](#empty) `()` .

### <a name="example"></a>Exemple

```cpp
// cliext_queue_size.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="queuesize_type-stlclr"></a><a name="size_type"></a> queue :: size_type (STL/CLR)

Type d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments non négatifs.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_size_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myqueue::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
a b c
size difference = 2
```

## <a name="queueto_array-stlclr"></a><a name="to_array"></a> queue :: to_array (STL/CLR)

Copie la séquence contrôlée dans un nouveau tableau.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un tableau contenant la séquence contrôlée. Vous l’utilisez pour obtenir une copie de la séquence contrôlée sous forme de tableau.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_to_array.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c d
a b c
```

## <a name="queuevalue_type-stlclr"></a><a name="value_type"></a> queue :: value_type (STL/CLR)

Type d’un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la *valeur* de paramètre de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_value_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Myqueue::value_type val = c1.front();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-queue-stlclr"></a><a name="op_neq"></a> Operator ! = (file d’attente) (STL/CLR)

Comparaison n’est pas égale à la file d’attente.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator!=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `!(left == right)` . Vous l’utilisez pour tester si *Left* n’est pas *ordonné de la même manière que* si les deux files d’attente sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_operator_ne.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-queue-stlclr"></a><a name="op_lt"></a> opérateur &lt; (file d’attente) (STL/CLR)

File d’attente inférieure à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator<(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction operator retourne true si, pour la position la plus basse `i` pour laquelle `!(right[i] < left[i])` elle est également true `left[i] < right[i]` . Dans le cas contraire, elle retourne `left->` [queue :: Size (STL/CLR)](#size) `() <` `right->size()` que vous utilisez  pour déterminer si Left  est ordonné avant le moment où les deux files d’attente sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_operator_lt.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-queue-stlclr"></a><a name="op_lteq"></a> opérateur &lt; = (file d’attente) (STL/CLR)

Comparaison de la file d’attente inférieure ou égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator<=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `!(right < left)` . Vous l’utilisez pour tester si *Left* n’est pas trié après *le* moment où les deux files d’attente sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_operator_le.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-queue-stlclr"></a><a name="op_eq"></a> opérateur = = (file d’attente) (STL/CLR)

Comparaison égale à la file d’attente.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator==(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction operator retourne true uniquement si les séquences contrôlées par *Left* et *Right* ont la même longueur et, pour chaque position `i` , `left[i] ==` `right[i]` . Vous l’utilisez pour tester si *Left* est *ordonné de la même façon que* lorsque les deux files d’attente sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_operator_eq.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-queue-stlclr"></a><a name="op_gt"></a> opérateur &gt; (file d’attente) (STL/CLR)

File d’attente supérieure à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator>(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `right` `<` `left` . Vous l’utilisez pour tester si *Left* est trié après *le* moment où les deux files d’attente sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_operator_gt.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-queue-stlclr"></a><a name="op_gteq"></a> opérateur &gt; = (file d’attente) (STL/CLR)

Comparaison de la file d’attente supérieure ou égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator>=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `!(left < right)` . Vous l’utilisez pour tester si *Left* n’est pas trié *avant le moment où* les deux files d’attente sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_queue_operator_ge.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
