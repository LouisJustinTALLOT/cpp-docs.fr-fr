---
title: priority_queue (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 573b365e0ca0d1c5b607144b1d143796e1ce927c
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42572463"
---
# <a name="priorityqueue-stlclr"></a>priority_queue (STL/CLR)
La classe de modèle décrit un objet qui contrôle une longueur variable ordonné séquence d’éléments qui a un accès limité. Utilisation de l’adaptateur de conteneur `priority_queue` pour gérer un conteneur sous-jacent comme une file d’attente de priorité.  
  
 Dans la description ci-dessous, `GValue` est identique à *valeur* , sauf si ce dernier est un type ref, auquel cas il est `Value^`. De même, `GContainer` est identique à *conteneur* , sauf si ce dernier est un type ref, auquel cas il est `Container^`.  
  
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
 *Valeur*  
 Type d'un élément dans la séquence contrôlée.  
  
 *Conteneur*  
 Type du conteneur sous-jacent.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<cliext/file d’attente >  
  
 **Namespace :** cliext  

## <a name="declarations"></a>Déclarations  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[priority_queue::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|  
|[priority_queue::container_type (STL/CLR)](#container_type)|Type du conteneur sous-jacent.|  
|[priority_queue::difference_type (STL/CLR)](#difference_type)|Type d'une distance signée entre deux éléments.|  
|[priority_queue::generic_container (STL/CLR)](#generic_container)|Le type de l’interface générique pour l’adaptateur de conteneur.|  
|[priority_queue::generic_value (STL/CLR)](#generic_value)|Le type d’un élément pour l’interface générique pour l’adaptateur de conteneur.|  
|[priority_queue::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|  
|[priority_queue::size_type (STL/CLR)](#size_type)|Type d'une distance signée entre deux éléments.|  
|[priority_queue::value_compare (STL/CLR)](#value_compare)|Délégué de classement pour deux éléments.|  
|[priority_queue::value_type (STL/CLR)](#value_type)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[priority_queue::assign (STL/CLR)](#assign)|Remplace tous les éléments.|  
|[priority_queue::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|  
|[priority_queue::get_container (STL/CLR)](#get_container)|Accède au conteneur sous-jacent.|  
|[priority_queue::pop (STL/CLR)](#pop)|Supprime l’élément de priorité hghest.|  
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|Construit un objet conteneur.|  
|[priority_queue::push (STL/CLR)](#push)|Ajoute un nouvel élément.|  
|[priority_queue::size (STL/CLR)](#size)|Compte le nombre d'éléments.|  
|[priority_queue::top (STL/CLR)](#top)|Accède à l’élément de priorité la plus élevée.|  
|[priority_queue::to_array (STL/CLR)](#to_array)|Copie la séquence contrôlée vers un nouveau tableau.|  
|[priority_queue::value_comp (STL/CLR)](#value_comp)|Copie le délégué de classement pour deux éléments.|  
  
|Propriété|Description|  
|--------------|-----------------|  
|[priority_queue::top_item (STL/CLR)](#top_item)|Accède à l’élément de priorité la plus élevée.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[priority_queue::operator= (STL/CLR)](#op_as)|Remplace la séquence contrôlée.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|IPriorityQueue\<valeur, le conteneur >|Mettre à jour d’adaptateur de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un conteneur sous-jacent, de type `Container`, qui stocke `Value` éléments et se développe sur la demande. Il conserve la séquence classée en tant que segment, avec l’élément de priorité la plus élevée (l’élément supérieur) facilement accessible et amovible. L’objet limite l’accès à envoyer de nouveaux éléments et en dépilant simplement l’élément de priorité la plus élevée, mise en œuvre d’une file d’attente de priorité.  
  
 L’objet trie la séquence qu’il contrôle en appelant un objet délégué stockée de type [priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stockées lorsque vous construisez l’objet priority_queue ; Si vous ne spécifiez aucun objet de délégué, la valeur par défaut est la comparaison `operator<(value_type, value_type)`. Vous accéder à cet objet stocké en appelant la fonction membre [priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`.  
  
 Cet objet de délégué doit imposer un ordre faible strict sur les valeurs de type [priority_queue::value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md). Cela signifie que, pour toutes les deux clés `X` et `Y`:  
  
 `value_comp()(X, Y)` Retourne la valeur booléenne même résultat à chaque appel.  
  
 Si `value_comp()(X, Y)` est true, puis `value_comp()(Y, X)` doit avoir la valeur false.  
  
 Si `value_comp()(X, Y)` est true, puis `X` est dit être ordonnées avant `Y`.  
  
 Si `!value_comp()(X, Y) && !value_comp()(Y, X)` est true, puis `X` et `Y` sont réputées pour avoir un classement équivalent.  
  
 Pour tout élément `X` qui précède `Y` dans la séquence contrôlée, `key_comp()(Y, X)` a la valeur false. (Pour l’objet de délégué par défaut, les clés va jamais en diminuant valeur.)  
  
 L’élément de priorité la plus élevée est donc un des éléments qui n’est pas classé avant tout autre élément.  
  
 Étant donné que le conteneur sous-jacent conserve les éléments classés comme un segment de mémoire :  
  
 Le conteneur doit prendre en charge des itérateurs d’accès aléatoire.  
  
 Éléments avec un classement équivalent peuvent être dépilés dans un ordre différent, qu’ils ont été transmis par push. (L’ordre n’est pas stable.)  
  
 Par conséquent, incluent des candidats pour le conteneur sous-jacent [deque (STL/CLR)](../dotnet/deque-stl-clr.md) et [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md).  
  
## <a name="members"></a>Membres
  
## <a name="assign"></a> priority_queue::Assign (STL/CLR)
Remplace tous les éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void assign(priority_queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *right*  
 Adaptateur de conteneur à insérer.  
  
### <a name="remarks"></a>Notes  
 La fonction membre assigne `right.get_container()` au conteneur sous-jacent. Il permet de modifier tout le contenu de la file d’attente.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Mypriority_queue c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
c a b  
```  

## <a name="const_reference"></a> priority_queue::const_reference (STL/CLR)
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
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="container_type"></a> priority_queue::container_type (STL/CLR)
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
```  

## <a name="difference_type"></a> priority_queue::difference_type (STL/CLR)
Les types d’une distance signée entre deux éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un nombre d’éléments éventuellement négatif.  
  
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
        System::Console::Write(" {0}", elem);   
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

## <a name="empty"></a> priority_queue::Empty (STL/CLR)
Vérifie l'absence d'éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la valeur true pour une séquence contrôlée vide. Il est équivalent à [priority_queue::size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)`() == 0`. Vous l’utilisez pour tester si l’objet priority_queue est vide.  
  
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
        System::Console::Write(" {0}", elem);   
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

## <a name="generic_container"></a> priority_queue::generic_container (STL/CLR)
Le type de l’interface générique pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>  
    generic_container;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit l’interface générique pour cette classe de l’adaptateur de conteneur de modèle.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mypriority_queue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->push(L'd');   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push(L'e');   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
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

## <a name="generic_value"></a> priority_queue::generic_value (STL/CLR)
Le type d’un élément pour une utilisation avec l’interface générique pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stockée pour une utilisation avec l’interface générique pour cette classe de conteneur de modèle. (`GValue` est soit `value_type` ou `value_type^` si `value_type` est un type ref.)  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Mypriority_queue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in priority order using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Mypriority_queue::generic_value elem = gc1->top();   
  
        System::Console::Write(" {0}", elem);   
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

## <a name="get_container"></a> priority_queue::get_container (STL/CLR)
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
```  

## <a name="op_as"></a> priority_queue::operator = (STL/CLR)
Remplace la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *right*  
 Adaptateur de conteneur à copier.  
  
### <a name="remarks"></a>Notes  
 Les copies d’opérateur membre *droit* à l’objet, puis retourne `*this`. Utilisez-le pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans *droit*.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mypriority_queue c2;   
    c2 = c1;   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
c a b  
c a b  
```  

## <a name="pop"></a> priority_queue::POP (STL/CLR)
Supprime l’élément le plus élevé proirity.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void pop();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre supprime l’élément de priorité la plus élevée de la séquence contrôlée, qui doit être non vide. Il permet de raccourcir la file d’attente d’un élément à l’arrière.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop();   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
b a  
```  

## <a name="priority_queue"></a> priority_queue::priority_queue (STL/CLR)
Construit un objet d’adaptateur de conteneur.  
  
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
 *suite*  
 Conteneur à copier.  
  
 *first*  
 Début de la plage à insérer.  
  
 *last*  
 Fin de la plage à insérer.  
  
 *Pred*  
 Classement de prédicat pour la séquence contrôlée.  
  
 *right*  
 Objet ou plage à insérer.  
  
### <a name="remarks"></a>Notes  
 Le constructeur :  
  
 `priority_queue();`  
  
 Crée un conteneur d’encapsulée vide, avec la valeur par défaut de classement de prédicat. Il permet de spécifier une séquence contrôlée initiale vide, avec la valeur par défaut de classement de prédicat.  
  
 Le constructeur :  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 Crée un conteneur encapsulé est une copie de `right.get_container()`, avec le prédicat de tri `right.value_comp()`. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de file d’attente *droit*, avec le même prédicat de tri.  
  
 Le constructeur :  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 Crée un conteneur encapsulé est une copie de `right->get_container()`, avec le prédicat de tri `right->value_comp()`. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de file d’attente `*right`, avec le même prédicat de tri.  
  
 Le constructeur :  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 Crée un conteneur vide encapsulé, avec le prédicat de tri *pred*. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide avec le prédicat de tri spécifié.  
  
 Le constructeur :  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 Crée un conteneur vide encapsulé, avec le prédicat de tri *pred*, puis exécute un push de tous les éléments de *suite* vous l’utilisez pour spécifier une séquence contrôlée initiale à partir d’un conteneur existant, avec le prédicat de tri spécifié.  
  
 Le constructeur :  
  
 `template<typename InIt> priority_queue(InIt first, InIt last);`  
  
 Crée un conteneur vide encapsulé, avec le prédicat de tri par défaut, puis exécute un push de la séquence [`first`, `last`). Vous l’utilisez pour spécifier une séquence contrôlée initiale à partir d’un eqeuence spécifié, avec le prédicat de tri spécifié.  
  
 Le constructeur :  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`  
  
 Crée un conteneur vide encapsulé, avec le prédicat de tri *pred*, puis exécute un push de la séquence [`first`, `last`). Vous l’utilisez pour spécifier une séquence contrôlée initiale à partir d’un seqeuence spécifié, avec le prédicat de tri spécifié.  
  
 Le constructeur :  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`  
  
 Crée un conteneur vide encapsulé, avec le prédicat de tri *pred*, puis exécute un push de tous les éléments de *suite* ainsi que la séquence [`first`, `last`). Vous l’utilisez pour spécifier une séquence contrôlée initiale à partir d’un conteneur existant et un seqeuence spécifié, avec le prédicat de tri spécifié.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    for each (wchar_t elem in wc1)   
        c2.push(elem);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule by copying an underlying container   
    Mypriority_queue c2x =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
   for each (wchar_t elem in c2x.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mypriority_queue c3(wc1->begin(), wc1->end());   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mypriority_queue c4(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>());   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range, another container, and an ordering rule   
    Mypriority_queue c5(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c5.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mypriority_queue c6(c3);   
    for each (wchar_t elem in c6.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mypriority_queue c7(%c3);   
    for each (wchar_t elem in c7.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule, by copying an underlying container   
    Mypriority_queue c8 =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c8.get_container())   
        System::Console::Write(" {0}", elem);   
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
  
## <a name="push"></a> priority_queue::push (STL/CLR)
Ajoute un nouvel élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void push(value_type val);  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre insère un élément avec la valeur `val` dans la séquence contrôlée et réorganise la séquence contrôlée pour maintenir la discipline du tas. Il permet d’ajouter un autre élément à la file d’attente.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
```  
  
## <a name="reference"></a> priority_queue::Reference (STL/CLR)
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify top of priority_queue and redisplay   
    Mypriority_queue::reference ref = c1.top();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
x a b  
```  

## <a name="size"></a> priority_queue::Size (STL/CLR)
Compte le nombre d'éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la longueur de la séquence contrôlée. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si vous intéresse est si la séquence a une taille différente de zéro, consultez [priority_queue::empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)`()`.  
  
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
        System::Console::Write(" {0}", elem);   
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

## <a name="size_type"></a> priority_queue::size_type (STL/CLR)
Le type d’une distance signée entre deux éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un nombre d’éléments de non négatif.  
  
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
        System::Console::Write(" {0}", elem);   
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
  
## <a name="to_array"></a> priority_queue::to_array (STL/CLR)
Copie la séquence contrôlée vers un nouveau tableau.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
d c b a  
c a b  
```  

## <a name="top"></a> priority_queue::Top (STL/CLR)
Accède à l’élément de priorité la plus élevée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reference top();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne une référence à l’élément supérieur (priorité la plus élevée) de la séquence contrôlée, qui doit être non vide. Vous l’utilisez pour accéder à l’élément de priorité la plus élevée, lorsque vous savez qu’il existe.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top() = {0}", c1.top());   
  
// alter last item and reinspect   
    c1.top() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  

## <a name="top_item"></a> priority_queue::top_item (STL/CLR)
Accède à l’élément de priorité la plus élevée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property value_type back_item;  
```  
  
### <a name="remarks"></a>Notes  
 La propriété accède à l’élément supérieur (priorité la plus élevée) de la séquence contrôlée, qui doit être non vide. Vous l’utilisez pour lire ou écrire l’élément de priorité la plus élevée, lorsque vous savez qu’il existe.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top_item = {0}", c1.top_item);   
  
// alter last item and reinspect   
    c1.top_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 c a b  
top_item = c  
 x a b  
```  

## <a name="value_comp"></a> priority_queue::value_comp (STL/CLR)
Copie le délégué de classement pour deux éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le délégué de classement utilisé pour ordonner la séquence contrôlée. Vous l’utilisez pour comparer deux valeurs.  
  
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

## <a name="value_compare"></a> priority_queue::value_compare (STL/CLR)
Délégué de classement pour les deux valeurs.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
binary_delegate<value_type, value_type, int> value_compare;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme pour le délégué qui détermine si le premier argument est classé avant le deuxième.  
  
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

## <a name="value_type"></a> priority_queue::Value_type (STL/CLR)
Type d’un élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle *valeur*.  
  
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
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  