---
title: vecteur (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
dev_langs:
- C++
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5d5b3e94b0b594174538aebe6542b04df7214f1b
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079810"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence à longueur variable d’éléments ayant un accès aléatoire. Vous utilisez le conteneur `vector` pour gérer une séquence d’éléments comme un bloc contigu de stockage. Le bloc est implémenté comme un tableau dont la taille augmente à la demande.  
  
 Dans la description ci-dessous, `GValue` est identique à `Value` , sauf si ce dernier est un type référence, auquel cas il est `Value^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>Paramètres  
 Value  
 Type d'un élément dans la séquence contrôlée.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<cliext/vector >  
  
 **Namespace :** cliext  

## <a name="declarations"></a>Déclarations  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[vector::const_iterator (STL/CLR)](#const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[vector::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|  
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Type d'un itérateur inserve constant pour la séquence contrôlée.|  
|[vector::difference_type (STL/CLR)](#difference_type)|Type d'une distance signée entre deux éléments.|  
|[vector::generic_container (STL/CLR)](#generic_container)|Le type de l’interface générique pour le conteneur.|  
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|Le type d’un itérateur pour l’interface générique pour le conteneur.|  
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|  
|[vector::generic_value (STL/CLR)](#generic_value)|Le type d’un élément pour l’interface générique pour le conteneur.|  
|[vector::iterator (STL/CLR)](#iterator)|Type d'un itérateur pour la séquence contrôlée.|  
|[vector::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|  
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|Type d'un itérateur inverse pour la séquence contrôlée.|  
|[vector::size_type (STL/CLR)](#size_type)|Type d'une distance signée entre deux éléments.|  
|[vector::value_type (STL/CLR)](#value_type)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[vector::assign (STL/CLR)](#assign)|Remplace tous les éléments.|  
|[vector::at (STL/CLR)](#at)|Accède à un élément à une position spécifiée.|  
|[vector::back (STL/CLR)](#back)|Accède au dernier élément.|  
|[vector::begin (STL/CLR)](#begin)|Désigne le début de la séquence contrôlée.|  
|[vector::capacity (STL/CLR)](#capacity)|Indique la taille de stockage alloué pour le conteneur.|  
|[vector::clear (STL/CLR)](#clear)|Supprime tous les éléments.|  
|[vector::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|  
|[vector::end (STL/CLR)](#end)|Désigne la fin de la séquence contrôlée.|  
|[vector::erase (STL/CLR)](#erase)|Supprime les éléments placés aux positions spécifiées.|  
|[vector::front (STL/CLR)](#front)|Accède au premier élément.|  
|[vector::insert (STL/CLR)](#insert)|Ajoute des éléments à la position spécifiée.|  
|[vector::pop_back (STL/CLR)](#pop_back)|Supprime le dernier élément.|  
|[vector::push_back (STL/CLR)](#push_back)|Ajoute un nouvel élément en dernier.|  
|[vector::rbegin (STL/CLR)](#rbegin)|Désigne le début de la séquence contrôlée inverse.|  
|[vector::rend (STL/CLR)](#rend)|Désigne la fin de la séquence contrôlée inverse.|  
|[vector::reserve (STL/CLR)](#reserve)|Garantit une capacité minimale de croissance pour le conteneur.|  
|[vector::resize (STL/CLR)](#resize)|Modifie le nombre d’éléments.|  
|[vector::size (STL/CLR)](#size)|Compte le nombre d'éléments.|  
|[vector::swap (STL/CLR)](#swap)|Échange le contenu de deux conteneurs.|  
|[vector::to_array (STL/CLR)](#to_array)|Copie de la séquence contrôlée vers un nouveau tableau.|  
|[vector::vector (STL/CLR)](#vector)|Construit un objet conteneur.|  
  
|Propriété|Description|  
|--------------|-----------------|  
|[vector::back_item (STL/CLR)](#back_item)|Accède au dernier élément.|  
|[vector::front_item (STL/CLR)](#front_item)|Accède au premier élément.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[vector::operator= (STL/CLR)](#op_as)|Remplace la séquence contrôlée.|  
|[vector::operator(STL/CLR)](#op)|Accède à un élément à une position spécifiée.|  
|[operator!= (vector) (STL/CLR)](#op_neq)|Détermine si un `vector` objet n’est pas égal à un autre `vector` objet.|  
|[operator< (vector) (STL/CLR)](#op_lt)|Détermine si un `vector` objet est inférieur à un autre `vector` objet.|  
|[operator<= (vector) (STL/CLR)](#op_lteq)|Détermine si un `vector` objet est inférieur ou égal à un autre `vector` objet.|  
|[operator== (vector) (STL/CLR)](#op_eq)|Détermine si un `vector` objet est égal à un autre `vector` objet.|  
|[operator> (vector) (STL/CLR)](#op_gt)|Détermine si un `vector` objet est supérieur à un autre `vector` objet.|  
|[operator>= (vector) (STL/CLR)](#op_gteq)|Détermine si un `vector` objet est supérieur ou égal à un autre `vector` objet.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|<xref:System.Collections.IEnumerable>|Dans les éléments de séquence.|  
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Séquence via les éléments typés.|  
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|  
|<xref:System.Collections.Generic.IList%601>|Mettre à jour un groupe ordonné d’éléments typés.|  
|IVector < valeur\>|Mettre à jour de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un tableau stocké de `Value` éléments, ce qui se développe sur la demande. Croissance se produit de manière à ce que le coût de l’ajout d’un nouvel élément est le temps fixe amorti. En d’autres termes, le coût de l’ajout d’éléments à la fin n’augmente pas, en moyenne, en tant que la longueur des séquence contrôlée est élevé. Par conséquent, un vecteur est un bon candidat pour le conteneur sous-jacent pour la classe de modèle [pile (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 A `vector` itérateurs prend en charge l’accès aléatoire, ce qui signifie que vous pouvez faire référence à un élément donné directement de sa position numérique, en partant de zéro pour le premier élément (avant), à `size() - 1` pour le dernier élément (arrière). Cela signifie également qu’un vecteur est un bon candidat pour le conteneur sous-jacent pour la classe de modèle [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Un itérateur de vecteur stocke un handle vers son objet de vecteur associés, ainsi que le décalage de l’élément qu’il désigne. Vous pouvez utiliser des itérateurs uniquement avec les objets du conteneur associé. Le décalage d’un élément de vecteur est identique à sa position.  
  
 Insertion ou la suppression d’éléments pouvez modifier la valeur d’élément stockée à une position donnée, de sorte que la valeur désignée par un itérateur peut également changer. (Le conteneur peut avoir à copier des éléments ou vers le bas pour créer une faille d’avant une opération d’insertion ou de remplissage d’un trou après un effacement.) Toutefois, un itérateur de vecteur reste valide tant que son décalage est dans la plage `[0, size()]`. En outre, un itérateur valide reste dereferencable--vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne--tant que son décalage n’est pas égal à `size()`.  
  
 Effacement ou suppression d’un élément appelle le destructeur de sa valeur stockée. Destruction du conteneur efface tous les éléments. Par conséquent, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne survivent le conteneur. Notez, toutefois, qu’un conteneur de handles ne détruit pas ses éléments.  
  
## <a name="members"></a>Membres

## <a name="assign"></a> Vector::Assign (STL/CLR)
Remplace tous les éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 count  
 Nombre d’éléments à insérer.  
  
 premier  
 Début de la plage à insérer.  
  
 last  
 Fin de la plage à insérer.  
  
 droite  
 Énumération à insérer.  
  
 Val  
 Valeur de l’élément à insérer.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre remplace la séquence contrôlée par une répétition de `count` éléments ayant la valeur `val`. Utilisez-le pour remplir le conteneur avec des éléments dont la même valeur.  
  
 Si `InIt` est de type entier, la deuxième fonction membre comporte comme `assign((size_type)first, (value_type)last)`. Dans le cas contraire, elle remplace la séquence contrôlée par la séquence [`first`, `last`). Utilisez-le pour rendre le contrôlée une copie de la séquence une autre séquence.  
  
 La troisième fonction membre remplace la séquence contrôlée par la séquence de désignée par l’énumérateur `right`. Il permet d’effectuer la séquence contrôlée une copie d’une séquence décrite par l’énumérateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_assign.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  

## <a name="at"></a> Vector::AT (STL/CLR)
Accède à un élément à une position spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference at(size_type pos);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pos  
 Position de l'élément auquel accéder.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne une référence à l’élément de la séquence contrôlée à la position `pos`. Vous l’utilisez pour lire ou écrire un élément dont la position vous connaissez.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_at.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using at   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1.at(1) = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  

## <a name="back"></a> Vector::Back (STL/CLR)
Accède au dernier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference back();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne une référence au dernier élément de la séquence contrôlée, qui doit être vide. Il permet d’accéder au dernier élément, lorsque vous savez qu’il existe.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back() = c  
 a b x  
```  

## <a name="back_item"></a> Vector::back_item (STL/CLR)
Accède au dernier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
property value_type back_item;  
```  
  
### <a name="remarks"></a>Notes  
 La propriété accède le dernier élément de la séquence contrôlée, qui doit être vide. Vous l’utilisez pour lire ou écrire le dernier élément, lorsque vous savez qu’il existe.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_back_item.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  

## <a name="begin"></a> Vector::Begin (STL/CLR)
Désigne le début de la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur à accès aléatoire qui désigne le premier élément de la séquence contrôlée ou juste après la fin d’une séquence vide. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` début de la séquence contrôlée, mais son état peut changer si la longueur de la séquence contrôlée change.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_begin.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
 x y c  
```  

## <a name="capacity"></a> Vector::Capacity (STL/CLR)
Indique la taille de stockage alloué pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
size_type capacity();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le stockage actuellement alloué pour la séquence contrôlée, une valeur au moins aussi grande que [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`. Il permet de déterminer la quantité le conteneur peut croître avant qu’il doit réallouer le stockage pour la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_capacity.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  

## <a name="clear"></a> Vector::Clear (STL/CLR)
Supprime tous les éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre appelle [vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(` [vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md) `(),` [vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `())`. Il permet de vous assurer que la séquence contrôlée est vide.  
  
### <a name="example"></a>Exemple  
  
```  
// cliext_vector_clear.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  

## <a name="const_iterator"></a> Vector::const_iterator (STL/CLR)
Type d'un itérateur constant pour la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type non spécifié `T2` qui peut servir d’un itérateur à accès aléatoire constant pour la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_const_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> Vector::const_reference (STL/CLR)
Type d'une référence constante à un élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit une référence constante à un élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_const_reference.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        cliext::vector<wchar_t>::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> Vector::const_reverse_iterator (STL/CLR)
Le type d’un itérateur inverse constant pour la séquence contrôlée...  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type non spécifié `T4` qui peut servir d’un itérateur inverse constant pour la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="difference_type"></a> Vector::difference_type (STL/CLR)
Les types d’une distance signée entre deux éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un nombre d’éléments signés.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_difference_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::vector<wchar_t>::difference_type diff = 0;   
    for (cliext::vector<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it) ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (cliext::vector<wchar_t>::iterator it = c1.end();   
        it != c1.begin(); --it) --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> Vector::Empty (STL/CLR)
Vérifie l'absence d'éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la valeur true pour une séquence contrôlée vide. Elle est équivalente à [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() == 0`. Il permet de tester si le vecteur est vide.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_empty.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
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

## <a name="end"></a> Vector::end (STL/CLR)
Désigne la fin de la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur à accès aléatoire qui pointe juste après la fin de la séquence contrôlée. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` fin de la séquence contrôlée, mais son état peut changer si la longueur de la séquence contrôlée change.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_end.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::vector<wchar_t>::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
 a x y  
```  

## <a name="erase"></a> Vector::Erase (STL/CLR)
Supprime les éléments placés aux positions spécifiées.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Paramètres  
 premier  
 Début de la plage à effacer.  
  
 last  
 Fin de la plage à effacer.  
  
 où  
 Élément à effacer.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre supprime l’élément de la séquence contrôlée vers lequel pointé `where`. Il permet de supprimer un seul élément.  
  
 La deuxième fonction membre supprime l’élément de la séquence contrôlée dans la plage [`first`, `last`). Il permet de supprimer de zéro ou plusieurs éléments contigus.  
  
 Les deux fonctions membres retournent un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou [vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `()` si cet élément n’existe.  
  
 Lorsque vous supprimez des éléments, le nombre de copies de l’élément est linéaire quant au nombre d’éléments entre la fin de la suppression et la fin la plus proche de la séquence. (Lorsque vous supprimez un ou plusieurs éléments à chaque extrémité de la séquence, aucune copie de l’élément se produit.)  
  
### <a name="example"></a>Exemple  
  
```cpp 
// cliext_vector_erase.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::vector<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  

## <a name="front"></a> Vector::Front (STL/CLR)
Accède au premier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference front();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne une référence au premier élément de la séquence contrôlée, qui doit être vide. Vous l’utilisez pour lire ou écrire le premier élément, lorsque vous savez qu’il existe.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_front.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front() = a  
 x b c  
```  

# <a name="front_item"></a> Vector::front_item (STL/CLR)
Accède au premier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
property value_type front_item;  
```  
  
### <a name="remarks"></a>Notes  
 La propriété accède au premier élément de la séquence contrôlée, qui doit être vide. Vous l’utilisez pour lire ou écrire le premier élément, lorsque vous savez qu’il existe.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_front_item.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter first item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  

# <a name="generic_container"></a> Vector::generic_container (STL/CLR)
Le type de l’interface générique pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef Microsoft::VisualC::StlClr::  
    IVector<generic_value>  
    generic_container;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit l’interface générique pour cette classe de conteneur de modèle.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_generic_container.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(gc1->end(), L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push_back(L'e');   
  
    System::Collections::IEnumerator^ enum1 =   
        gc1->GetEnumerator();   
    while (enum1->MoveNext())   
        System::Console::Write(" {0}", enum1->Current);   
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

## <a name="generic_iterator"></a> Vector::generic_iterator (STL/CLR)
Le type d’un itérateur pour une utilisation avec l’interface générique pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerRandomAccessIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un itérateur générique qui peut être utilisé avec l’interface générique pour cette classe de conteneur de modèle.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

# <a name="generic_reverse_iterator"></a> Vector::generic_reverse_iterator (STL/CLR)
Le type d’un itérateur inverse pour une utilisation avec l’interface générique pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un itérateur inverse générique qui peut être utilisé avec l’interface générique pour cette classe de conteneur de modèle.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a c c  
```  

## <a name="generic_value"></a> Vector::generic_value (STL/CLR)
Le type d’un élément pour une utilisation avec l’interface générique pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stocké pour une utilisation avec l’interface générique pour cette classe de conteneur de modèle.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_generic_value.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

## <a name="insert"></a> Vector::Insert (STL/CLR)
Ajoute des éléments à la position spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 count  
 Nombre d’éléments à insérer.  
  
 premier  
 Début de la plage à insérer.  
  
 last  
 Fin de la plage à insérer.  
  
 droite  
 Énumération à insérer.  
  
 Val  
 Valeur de l’élément à insérer.  
  
 où  
 Emplacement dans le conteneur à insérer avant.  
  
### <a name="remarks"></a>Notes  
 Chaque membre fonctions insertions, avant l’élément vers lequel pointé `where` dans la séquence contrôlée, une séquence spécifiée par les opérandes restants.  
  
 La première fonction membre insère un élément avec la valeur `val` et retourne un itérateur qui désigne l’élément nouvellement inséré. Il permet d’insérer un élément unique avant un endroit désigné par un itérateur.  
  
 La deuxième fonction membre insère une répétition de `count` éléments ayant la valeur `val`. Il permet d’insérer des éléments contigus zéro ou plus qui sont toutes les copies de la même valeur.  
  
 Si `InIt` est un type entier, la troisième fonction membre se comporte comme `insert(where, (size_type)first, (value_type)last)`. Dans le cas contraire, il insère la séquence [`first`, `last`). Il permet d’insérer de zéro ou plusieurs éléments contigus, copiés à partir d’une autre séquence.  
  
 La quatrième fonction membre insère la séquence désignée par le `right`. Il permet d’insérer une séquence décrite par l’énumérateur.  
  
 Lors de l’insertion d’un élément unique, le nombre de copies de l’élément est linéaire quant au nombre d’éléments entre le point d’insertion et la fin la plus proche de la séquence. (Lors de l’insertion d’un ou plusieurs éléments à chaque extrémité de la séquence, aucune copie de l’élément se produit.) Si `InIt` est un itérateur d’entrée, la troisième fonction membre exécute en réalité une insertion unique pour chaque élément dans la séquence. Sinon, lors de l’insertion `N` éléments, le nombre de copies de l’élément est linéaire dans `N` plus le nombre d’éléments entre le point d’insertion et la fin la plus proche de la séquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_insert.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  
  
## <a name="iterator"></a> Vector::iterator (STL/CLR)
Type d'un itérateur pour la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type non spécifié `T1` qui peut servir d’itérateur à accès aléatoire pour la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    it = c1.begin();   
    *it = L'x';   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x b c  
```  

## <a name="op_as"></a> Vector::operator = (STL/CLR)
Remplace la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
vector<Value>% operator=(vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Conteneur à copier.  
  
### <a name="remarks"></a>Notes  
 Les copies d’opérateur de membre `right` à l’objet, puis retourne `*this`. Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans `right`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_operator_as.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="op"></a> Vector::operator(STL/CLR)
Accède à un élément à une position spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference operator[](size_type pos);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pos  
 Position de l'élément auquel accéder.  
  
### <a name="remarks"></a>Notes  
 L’opérateur membre retourne un referene à l’élément à la position `pos`. Il permet d’accéder à un élément dont vous connaissez la position.  
  
### <a name="example"></a>Exemple  
  
```cpp 
// cliext_vector_operator_sub.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using subscripting   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1[1] = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  

## <a name="pop_back"></a> Vector::pop_back (STL/CLR)
Supprime le dernier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void pop_back();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre supprime le dernier élément de la séquence contrôlée, qui doit être vide. Il permet de raccourcir le vecteur d’un élément à l’arrière.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_pop_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b  
```  

## <a name="push_back"></a> Vector::push_back (STL/CLR)
Ajoute un nouvel élément en dernier.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void push_back(value_type val);  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre insère un élément avec la valeur `val` à la fin de la séquence contrôlée. Il permet d’ajouter un autre élément dans le vecteur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_push_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="rbegin"></a> Vector::rbegin (STL/CLR)
Désigne le début de la séquence contrôlée inverse.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur inverse qui désigne le dernier élément de la séquence contrôlée, ou juste après le début d’une séquence vide. Par conséquent, il désigne le `beginning` de la séquence inverse. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` début de la séquence contrôlée vue dans l’ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_rbegin.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
 a y x  
```  

## <a name="reference"></a> Vector::Reference (STL/CLR)
Type d'une référence à un élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit une référence à un élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_reference.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::vector<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::vector<wchar_t>::reference ref = *it;   
  
        ref += (wchar_t)(L'A' - L'a');   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
A B C  
```  

## <a name="rend"></a> Vector::rend (STL/CLR)
Désigne la fin de la séquence contrôlée inverse.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur inverse qui pointe juste après le début de la séquence contrôlée. Par conséquent, il désigne le `end` de la séquence inverse. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` fin de la séquence contrôlée vue dans l’ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_rend.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
 y x c  
```  

## <a name="reserve"></a> Vector::reserve (STL/CLR)
Garantit une capacité minimale de croissance pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void reserve(size_type count);  
```  
  
#### <a name="parameters"></a>Paramètres  
 count  
 Nouvelle capacité minimale du conteneur.  
  
### <a name="remarks"></a>Notes  
 La fonction membre garantit que `capacity()` dorénavant retourne au moins `count`. Il permet de vous assurer que le conteneur ne doive pas réaffecter le stockage pour la séquence contrôlée jusqu'à ce qu’il a atteint la taille spécifiée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_reserve.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  

## <a name="resize"></a> Vector::Resize (STL/CLR)
Modifie le nombre d’éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>Paramètres  
 NEW_SIZE  
 Nouvelle taille de la séquence contrôlée.  
  
 Val  
 Valeur de l’élément de remplissage.  
  
### <a name="remarks"></a>Notes  
 Les deux fonctions membres Vérifiez que [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()` retourne désormais `new_size`. Si elle doit rallonger la séquence contrôlée, la première fonction membre ajoute des éléments avec la valeur `value_type()`, tandis que la deuxième fonction membre ajoute des éléments avec la valeur `val`. Pour rendre la séquence contrôlée plus courte, les deux fonctions membres effacement efficacement le dernier élément [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size` fois. Vous l’utilisez pour vous assurer que la séquence contrôlée est de taille `new_size`, par la suppression ou la séquence contrôlée en cours de remplissage.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  

## <a name="reverse_iterator"></a> Vector::reverse_iterator (STL/CLR)
Type d'un itérateur inverse pour la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type non spécifié `T3` qui peut servir d’itérateur inverse pour la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
x b a  
```  

## <a name="size"></a> Vector::Size (STL/CLR)
Compte le nombre d'éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la longueur de la séquence contrôlée. Il permet de déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si tout vous intéressent est indique si la séquence a une taille différente de zéro, consultez [vector::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_size.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  

## <a name="size_type"></a> Vector::size_type (STL/CLR)
Type d'une distance signée entre deux éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un nombre non négatif élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_size_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  
  
## <a name="swap"></a> Vector::swap (STL/CLR)
Échange le contenu de deux conteneurs.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void swap(vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Conteneur avec lequel échanger le contenu.  
  
### <a name="remarks"></a>Notes  
 La fonction membre échange les séquences contrôlées entre `*this` et `right`. Cela se fait en temps constant et ne lève aucune exception. Vous l’utiliser comme un moyen rapide de l’échange le contenu de deux conteneurs.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_swap.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::vector<wchar_t> c2(5, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x x x x x  
x x x x x  
a b c  
```  

## <a name="to_array"></a> Vector::to_array (STL/CLR)
Copie de la séquence contrôlée vers un nouveau tableau.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un tableau contenant la séquence contrôlée. Il permet d’obtenir une copie de la séquence contrôlée sous forme de tableau.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_to_array.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push_back(L'd');   
    for each (wchar_t elem in c1)   
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
a b c d  
a b c  
```  

## <a name="value_type"></a> Vector::Value_type (STL/CLR)
Type d’un élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Value`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_value_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::vector<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::vector<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="vector"></a> Vector::Vector (STL/CLR)
Construit un objet conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 count  
 Nombre d’éléments à insérer.  
  
 premier  
 Début de la plage à insérer.  
  
 last  
 Fin de la plage à insérer.  
  
 droite  
 Objet ou plage à insérer.  
  
 Val  
 Valeur de l’élément à insérer.  
  
### <a name="remarks"></a>Notes  
 Le constructeur :  
  
 `vector();`  
  
 Initialise la séquence contrôlée sans aucun élément. Il permet de spécifier une séquence contrôlée initiale vide.  
  
 Le constructeur :  
  
 `vector(vector<Value>% right);`  
  
 Initialise la séquence contrôlée par la séquence [`right.begin()`, `right.end()`). Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet vector `right`.  
  
 Le constructeur :  
  
 `vector(vector<Value>^ right);`  
  
 Initialise la séquence contrôlée par la séquence [`right->begin()`, `right->end()`). Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de vecteur dont le handle est `right`.  
  
 Le constructeur :  
  
 `explicit vector(size_type count);`  
  
 Initialise la séquence contrôlée avec `count` éléments dont la valeur `value_type()`. Utilisez-le pour remplir le conteneur avec des éléments dont la valeur par défaut.  
  
 Le constructeur :  
  
 `vector(size_type count, value_type val);`  
  
 Initialise la séquence contrôlée avec `count` éléments dont la valeur `val`. Utilisez-le pour remplir le conteneur avec des éléments dont la même valeur.  
  
 Le constructeur :  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 Initialise la séquence contrôlée par la séquence [`first`, `last`). Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence.  
  
 Le constructeur :  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Initialise la séquence contrôlée par la séquence désignée par l’énumérateur `right`. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par l’énumérateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  

## <a name="op_neq"></a> opérateur ! = (vecteur) (STL/CLR)
Vecteur de comparaison n’est pas égal.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value>  
    bool operator!=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(left == right)`. Il permet de tester si `left` n’est pas ordonné identique `right` lorsque les deux vecteurs sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_operator_ne.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
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

## <a name="op_lt"></a> opérateur&lt; (vecteur) (STL/CLR)
Vecteur inférieure à la comparaison.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator<(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 L’opérateur fonction retourne true si, pour la position la plus basse `i` pour lequel `!(right[i] < left[i])` il est également vrai que `left[i] < right[i]`. Sinon, elle retourne `left->size() < right->size()` vous l’utiliser pour tester si `left` est classé avant `right` lorsque les deux vecteurs sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_operator_lt.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
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

## <a name="op_lteq"></a> opérateur&lt;= (vecteur) (STL/CLR)
Inférieur ou égal de vecteur comparaison.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator<=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(right < left)`. Il permet de tester si `left` n’est pas ordonné après `right` lorsque les deux vecteurs sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_operator_le.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
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

## <a name="op_eq"></a> opérateur == (vecteur) (STL/CLR)
Comparaison égale de vecteur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator==(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne true uniquement si les séquences contrôlées par `left` et `right` ont la même longueur et, pour chaque position `i`, `left[i] ==` `right[i]`. Il permet de tester si `left` est ordonné identique `right` lorsque les deux vecteurs sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_operator_eq.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
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

## <a name="op_gt"></a> opérateur&gt; (vecteur) (STL/CLR)
Comparaison de supériorité de vecteur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator>(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `right` `<` `left`. Il permet de tester si `left` est trié après `right` lorsque les deux vecteurs sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_operator_gt.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
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

## <a name="op_gteq"></a> opérateur&gt;= (vecteur) (STL/CLR)
Vecteur supérieur ou égal comparaison.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator>=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(left < right)`. Il permet de tester si `left` n’est pas classé avant `right` lorsque les deux vecteurs sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_vector_operator_ge.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
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
