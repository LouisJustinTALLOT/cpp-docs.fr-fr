---
title: Stack (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::stack::assign
- cliext::stack::const_reference
- cliext::stack::container_type
- cliext::stack::difference_type
- cliext::stack::empty
- cliext::stack::generic_container
- cliext::stack::generic_value
- cliext::stack::get_container
- cliext::stack::operator=
- cliext::stack::pop
- cliext::stack::push
- cliext::stack::reference
- cliext::stack::size
- cliext::stack::size_type
- cliext::stack::stack
- cliext::stack::to_array
- cliext::stack::top
- cliext::stack::top_item
- cliext::stack::value_type
dev_langs:
- C++
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
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
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- stack member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9e1138ff947599b3ece75224ae2120c6f4775bab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376874"
---
# <a name="stack-stlclr"></a>stack (STL/CLR)

La classe de modèle décrit un objet qui contrôle une séquence de longueur variable constituée d’éléments qui dispose d’un accès dernier sorti. Utilisation de l’adaptateur de conteneur `stack` pour gérer un conteneur sous-jacent comme une pile de push vers le bas.

Dans la description ci-dessous, `GValue` est identique à *valeur* , sauf si ce dernier est un type ref, auquel cas il est `Value^`. De même, `GContainer` est identique à *conteneur* , sauf si ce dernier est un type ref, auquel cas il est `Container^`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    ref class stack
        :   public
        System::ICloneable,
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>Paramètres

*Valeur*<br/>
Type d'un élément dans la séquence contrôlée.

*Conteneur*<br/>
Type du conteneur sous-jacent.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<cliext/pile >

**Namespace :** cliext

## <a name="declarations"></a>Déclarations

|Définition de types|Description|
|---------------------|-----------------|
|[stack::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|
|[stack::container_type (STL/CLR)](#container_type)|Type du conteneur sous-jacent.|
|[stack::difference_type (STL/CLR)](#difference_type)|Type d'une distance signée entre deux éléments.|
|[stack::generic_container (STL/CLR)](#generic_container)|Le type de l’interface générique pour l’adaptateur de conteneur.|
|[stack::generic_value (STL/CLR)](#generic_value)|Le type d’un élément pour l’interface générique pour l’adaptateur de conteneur.|
|[stack::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|
|[stack::size_type (STL/CLR)](#size_type)|Type d'une distance signée entre deux éléments.|
|[stack::value_type (STL/CLR)](#value_type)|Type d’un élément.|

|Fonction membre|Description|
|---------------------|-----------------|
|[stack::assign (STL/CLR)](#assign)|Remplace tous les éléments.|
|[stack::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|
|[stack::get_container (STL/CLR)](#get_container)|Accède au conteneur sous-jacent.|
|[stack::pop (STL/CLR)](#pop)|Supprime le dernier élément.|
|[stack::push (STL/CLR)](#push)|Ajoute un nouvel élément dernière.|
|[stack::size (STL/CLR)](#size)|Compte le nombre d'éléments.|
|[stack::stack (STL/CLR)](#stack)|Construit un objet conteneur.|
|[stack::top (STL/CLR)](#top)|Accède au dernier élément.|
|[stack::to_array (STL/CLR)](#to_array)|Copie la séquence contrôlée vers un nouveau tableau.|

|Propriété|Description|
|--------------|-----------------|
|[stack::top_item (STL/CLR)](#top_item)|Accède au dernier élément.|

|Opérateur|Description|
|--------------|-----------------|
|[stack::operator= (STL/CLR)](#op_as)|Remplace la séquence contrôlée.|
|[operator!= (stack) (STL/CLR)](#op_neq)|Détermine si un `stack` objet n’est pas égal à un autre `stack` objet.|
|[operator< (stack) (STL/CLR)](#op_lt)|Détermine si un `stack` objet est inférieur à un autre `stack` objet.|
|[operator<= (stack) (STL/CLR)](#op_lteq)|Détermine si un `stack` objet est inférieur ou égal à un autre `stack` objet.|
|[operator== (stack) (STL/CLR)](#op_eq)|Détermine si un `stack` objet est égal à un autre `stack` objet.|
|[operator> (stack) (STL/CLR)](#op_gt)|Détermine si un `stack` objet est supérieur à un autre `stack` objet.|
|[operator>= (stack) (STL/CLR)](#op_gteq)|Détermine si un `stack` objet est supérieur ou égal à un autre `stack` objet.|

## <a name="interfaces"></a>Interfaces

|Interface|Description|
|---------------|-----------------|
|<xref:System.ICloneable>|Dupliquer un objet.|
|IStack\<valeur, le conteneur >|Mettre à jour d’adaptateur de conteneur générique.|

## <a name="remarks"></a>Notes

L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un conteneur sous-jacent, de type *conteneur*, qui stocke *valeur* éléments et se développe sur la demande. L’objet limite l’accès à poussant et en dépilant simplement le dernier élément, mise en œuvre d’une file d’attente, last-in sorti (également appelé une file d’attente LIFO, ou stack).

## <a name="members"></a>Membres

## <a name="assign"></a> Stack::Assign (STL/CLR)

Remplace tous les éléments.

### <a name="syntax"></a>Syntaxe

```cpp
void assign(stack<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*right*<br/>
Adaptateur de conteneur à insérer.

### <a name="remarks"></a>Notes

La fonction membre assigne `right.get_container()` au conteneur sous-jacent. Il permet de modifier tout le contenu de la pile.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_assign.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign a repetition of values
    Mystack c2;
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

## <a name="const_reference"></a> Stack::const_reference (STL/CLR)

Type d'une référence constante à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence constante à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_const_reference.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mystack::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="container_type"></a> Stack::container_type (STL/CLR)

Type du conteneur sous-jacent.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *Container*.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_container_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Mystack::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="difference_type"></a> Stack::difference_type (STL/CLR)

Les types d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments éventuellement négatif.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_difference_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute negative difference
    Mystack::difference_type diff = c1.size();
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

## <a name="empty"></a> Stack::Empty (STL/CLR)

Vérifie l'absence d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur true pour une séquence contrôlée vide. Il est équivalent à [stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md)`() == 0`. Vous l’utilisez pour tester si la pile est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_empty.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="generic_container"></a> Stack::generic_container (STL/CLR)

Le type de l’interface générique pour l’adaptateur de conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::IStack<Value>
    generic_container;
```

### <a name="remarks"></a>Notes

Le type décrit l’interface générique pour cette classe de l’adaptateur de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_generic_container.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Mystack::generic_container^ gc1 = %c1;
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

## <a name="generic_value"></a> Stack::generic_value (STL/CLR)

Le type d’un élément pour une utilisation avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stockée pour une utilisation avec l’interface générique pour cette classe de conteneur de modèle. (`GValue` est soit `value_type` ou `value_type^` si `value_type` est un type ref.)

### <a name="example"></a>Exemple

```cpp
// cliext_stack_generic_value.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Mystack::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display in reverse using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mystack::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
c b a
```

## <a name="get_container"></a> Stack::get_container (STL/CLR)

Accède au conteneur sous-jacent.

### <a name="syntax"></a>Syntaxe

```cpp
container_type^ get_container();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un handle pour le conteneur sous-jacent. Vous l’utilisez pour ignorer les restrictions imposées par le wrapper de conteneur.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_get_container.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Mystack::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_as"></a> Stack::operator = (STL/CLR)

Remplace la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
stack <Value, Container>% operator=(stack <Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*right*<br/>
Adaptateur de conteneur à copier.

### <a name="remarks"></a>Notes

Les copies d’opérateur membre *droit* à l’objet, puis retourne `*this`. Utilisez-le pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans *droit*.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_operator_as.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="pop"></a> Stack::POP (STL/CLR)

Supprime le dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
void pop();
```

### <a name="remarks"></a>Notes

La fonction membre supprime le dernier élément de la séquence contrôlée, qui doit être non vide. Il permet de raccourcir la pile d’un élément à l’arrière.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_pop.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b
```

## <a name="push"></a> Stack::push (STL/CLR)

Ajoute un nouvel élément dernière.

### <a name="syntax"></a>Syntaxe

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Notes

La fonction membre insère un élément avec la valeur `val` à la fin de la séquence contrôlée. Il permet d’ajouter un autre élément à la pile.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_push.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="reference"></a> Stack::Reference (STL/CLR)

Type d'une référence à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_reference.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify top of stack and redisplay
    Mystack::reference ref = c1.top();
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

## <a name="size"></a> Stack::Size (STL/CLR)

Compte le nombre d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence contrôlée. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si vous intéresse est si la séquence a une taille différente de zéro, consultez [stack::empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md)`()`.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_size.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="size_type"></a> Stack::size_type (STL/CLR)

Le type d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments de non négatif.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_size_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Mystack::size_type diff = c1.size();
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

## <a name="stack"></a> Stack::Stack (STL/CLR)

Construit un objet d’adaptateur de conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
stack();
stack(stack<Value, Container>% right);
stack(stack<Value, Container>^ right);
explicit stack(container_type% wrapped);
```

#### <a name="parameters"></a>Paramètres

*right*<br/>
Objet à copier.

*encapsulé*<br/>
Conteneur encapsulée à utiliser.

### <a name="remarks"></a>Notes

Le constructeur :

`stack();`

Crée un conteneur vide encapsulé. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide.

Le constructeur :

`stack(stack<Value, Container>% right);`

Crée un conteneur encapsulé est une copie de `right.get_container()`. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de pile *droit*.

Le constructeur :

`stack(stack<Value, Container>^ right);`

Crée un conteneur encapsulé est une copie de `right->get_container()`. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de pile `*right`.

Le constructeur :

`explicit stack(container_type% wrapped);`

utilise le conteneur existant *encapsulé* comme conteneur encapsulé. Il permet de construire une pile à partir d’un conteneur existant.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_construct.cpp
// compile with: /clr
#include <cliext/stack>
#include <cliext/vector>

typedef cliext::stack<wchar_t> Mystack;
typedef cliext::vector<wchar_t> Myvector;
typedef cliext::stack<wchar_t, Myvector> Mystack_vec;
int main()
    {
// construct an empty container
    Mystack c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct from an underlying container
    Myvector v2(5, L'x');
    Mystack_vec c2(v2);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Mystack_vec c3(c2);
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container through handle
    Mystack_vec c4(%c2);
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

## <a name="to_array"></a> Stack::to_array (STL/CLR)

Copie la séquence contrôlée vers un nouveau tableau.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un tableau contenant la séquence contrôlée. Vous l’utilisez pour obtenir une copie de la séquence contrôlée sous forme de tableau.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_to_array.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="top"></a> Stack::Top (STL/CLR)

Accède au dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
reference top();
```

### <a name="remarks"></a>Notes

La fonction membre retourne une référence au dernier élément de la séquence contrôlée, qui doit être non vide. Vous l’utilisez pour accéder au dernier élément, lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_top.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

```Output
a b c
top() = c
a b x
```

## <a name="top_item"></a> Stack::top_item (STL/CLR)

Accède au dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type top_item;
```

### <a name="remarks"></a>Notes

La propriété accède le dernier élément de la séquence contrôlée, qui doit être non vide. Vous l’utilisez pour lire ou écrire le dernier élément lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_top_item.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b c
top_item = c
a b x
```

## <a name="value_type"></a> Stack::Value_type (STL/CLR)

Type d’un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *valeur*.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_value_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mystack::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="op_neq"></a> opérateur ! = (pile) (STL/CLR)

Comparaison différent de la pile.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator!=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction d’opérateur retourne `!(left == right)`. Il permet de tester si *gauche* n’est pas ordonné identique *droit* lorsque les deux piles sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_operator_ne.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="op_lt"></a> opérateur&lt; (pile) (STL/CLR)

Pile inférieur comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator<(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

L’opérateur fonction retourne true si, pour la position la plus basse `i` pour lequel `!(right[i] < left[i])` il est également vrai que `left[i] < right[i]`. Sinon, elle retourne `left->` [stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md) `() <` `right->size()` vous l’utiliser pour tester si *gauche* est classé avant *droite* Lorsque les deux piles sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_operator_lt.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="op_lteq"></a> opérateur&lt;= (pile) (STL/CLR)

Inférieur ou égal de pile comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator<=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction d’opérateur retourne `!(right < left)`. Il permet de tester si *gauche* n’est pas ordonné après *droit* lorsque les deux piles sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_operator_le.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="op_eq"></a> opérateur == (pile) (STL/CLR)

Pile de comparaison égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator==(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction d’opérateur retourne true uniquement si les séquences contrôlées par *gauche* et *droit* ont la même longueur et, pour chaque position `i`, `left[i] ==` `right[i]`. Il permet de tester si *gauche* est ordonné identique *droit* lorsque les deux piles sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_operator_eq.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="op_gt"></a> opérateur&gt; (pile) (STL/CLR)

Comparaison de supériorité de la pile.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator>(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction d’opérateur retourne `right` `<` `left`. Il permet de tester si *gauche* est trié après *droit* lorsque les deux piles sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_operator_gt.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="op_gteq"></a> opérateur&gt;= (pile) (STL/CLR)

Pile supérieur ou égal à comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    bool operator>=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction d’opérateur retourne `!(left < right)`. Il permet de tester si *gauche* n’est pas classé avant *droit* lorsque les deux piles sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_stack_operator_ge.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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