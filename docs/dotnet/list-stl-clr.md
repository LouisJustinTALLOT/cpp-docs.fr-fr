---
title: liste (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
dev_langs:
- C++
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
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
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8eb64c41db0e6062f2be636ddce7e8cefe0bb32b
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376288"
---
# <a name="list-stlclr"></a>list (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence de longueur variable constituée d’éléments qui dispose d’un accès bidirectionnel. Vous utilisez le conteneur `list` pour gérer une séquence d’éléments comme une liste liée bidirectionnelle de nœuds, chacun stocker un élément.  
  
 Dans la description ci-dessous, `GValue` est identique à *valeur* , sauf si ce dernier est un type ref, auquel cas il est `Value^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value>  
    ref class list  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        Microsoft::VisualC::StlClr::IList<GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>Paramètres  
 *Valeur*  
 Type d'un élément dans la séquence contrôlée.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext 

## <a name="declarations"></a>Déclarations  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[list::const_iterator (STL/CLR)](#const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[list::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|  
|[list::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Type d'un itérateur inserve constant pour la séquence contrôlée.|  
|[list::difference_type (STL/CLR)](#difference_type)|Type d'une distance signée entre deux éléments.|  
|[list::generic_container (STL/CLR)](#generic_container)|Le type de l’interface générique pour le conteneur.|  
|[list::generic_iterator (STL/CLR)](#generic_iterator)|Le type d’un itérateur pour l’interface générique pour le conteneur.|  
|[list::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|  
|[list::generic_value (STL/CLR)](#generic_value)|Le type d’un élément pour l’interface générique pour le conteneur.|  
|[list::iterator (STL/CLR)](#iterator)|Type d'un itérateur pour la séquence contrôlée.|  
|[list::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|  
|[list::reverse_iterator (STL/CLR)](#reverse_iterator)|Type d'un itérateur inverse pour la séquence contrôlée.|  
|[list::size_type (STL/CLR)](#size_type)|Type d'une distance signée entre deux éléments.|  
|[list::value_type (STL/CLR)](#value_type)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[list::assign (STL/CLR)](#assign)|Remplace tous les éléments.|  
|[list::back (STL/CLR)](#back)|Accède au dernier élément.|  
|[list::begin (STL/CLR)](#begin)|Désigne le début de la séquence contrôlée.|  
|[list::clear (STL/CLR)](#clear)|Supprime tous les éléments.|  
|[list::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|  
|[list::end (STL/CLR)](#end)|Désigne la fin de la séquence contrôlée.|  
|[list::erase (STL/CLR)](#erase)|Supprime les éléments placés aux positions spécifiées.|  
|[list::front (STL/CLR)](#front)|Accède au premier élément.|  
|[list::insert (STL/CLR)](#insert)|Ajoute des éléments à une position spécifiée.|  
|[list::list (STL/CLR)](#list)|Construit un objet conteneur.|  
|[list::merge (STL/CLR)](#merge)|Fusionne deux séquences contrôlées ordonnées.|  
|[list::pop_back (STL/CLR)](#pop_back)|Supprime le dernier élément.|  
|[list::pop_front (STL/CLR)](#pop_front)|Supprime le premier élément.|  
|[list::push_back (STL/CLR)](#push_back)|Ajoute un nouvel élément dernière.|  
|[list::push_front (STL/CLR)](#push_front)|Ajoute un nouvel élément de premier.|  
|[list::rbegin (STL/CLR)](#rbegin)|Désigne le début de la séquence contrôlée inverse.|  
|[list::remove (STL/CLR)](#remove)|Supprime un élément avec une valeur spécifiée.|  
|[list::remove_if (STL/CLR)](#remove_if)|Supprime les éléments qui réussissent un test spécifié.|  
|[list::rend (STL/CLR)](#rend)|Désigne la fin de la séquence contrôlée inverse.|  
|[list::resize (STL/CLR)](#resize)|Modifie le nombre d’éléments.|  
|[list::reverse (STL/CLR)](#reverse)|Inverse la séquence contrôlée.|  
|[list::size (STL/CLR)](#size)|Compte le nombre d'éléments.|  
|[list::sort (STL/CLR)](#sort)|Ordonne la séquence contrôlée.|  
|[list::splice (STL/CLR)](#splice)|Réassocie les liens entre les nœuds.|  
|[list::swap (STL/CLR)](#swap)|Échange le contenu de deux conteneurs.|  
|[list::to_array (STL/CLR)](#to_array)|Copie la séquence contrôlée vers un nouveau tableau.|  
|[list::unique (STL/CLR)](#unique)|Supprime des éléments adjacents qui réussissent un test spécifié.|  
  
|Propriété|Description|  
|--------------|-----------------|  
|[list::back_item (STL/CLR)](#back_item)|Accède au dernier élément.|  
|[list::front_item (STL/CLR)](#front_item)|Accède au premier élément.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[list::operator= (STL/CLR)](#op_as)|Remplace la séquence contrôlée.|  
|[operator!= (list) (STL/CLR)](#op_neq)|Détermine si un `list` objet n’est pas égal à un autre `list` objet.|  
|[operator< (list) (STL/CLR)](#op_lt)|Détermine si un `list` objet est inférieur à un autre `list` objet.|  
|[operator<= (list) (STL/CLR)](#op_lteq)|Détermine si un `list` objet est inférieur ou égal à un autre `list` objet.|  
|[operator== (list) (STL/CLR)](#op_eq)|Détermine si un `list` objet est égal à un autre `list` objet.|  
|[operator> (list) (STL/CLR)](#op_gt)|Détermine si un `list` objet est supérieur à un autre `list` objet.|  
|[operator>= (list) (STL/CLR)](#op_gteq)|Détermine si un `list` objet est supérieur ou égal à un autre `list` objet.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|<xref:System.Collections.IEnumerable>|Dans les éléments de séquence.|  
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Séquence via les éléments typés.|  
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|  
|IList\<valeur >|Mettre à jour de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle en tant que nœuds individuels dans une liste de liens bidirectionnel. Il réorganise les éléments en modifiant les liens entre les nœuds, jamais par copie le contenu d’un nœud à un autre. Cela signifie que vous pouvez insérer et supprimer des éléments librement sans perturber leurs éléments restants. Par conséquent, une liste est un bon candidat pour le conteneur sous-jacent pour la classe de modèle [file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md) ou classe de modèle [pile (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 Un `list` objet prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez exécuter pour les éléments adjacents, étant données un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud principal spécial correspond à l’itérateur retourné par [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`. Vous pouvez décrémenter cet itérateur afin d’atteindre le dernier élément dans la séquence contrôlée, le cas échéant. Vous pouvez incrémenter un itérateur de liste pour atteindre le nœud principal, et il compare ensuite égal à `end()`. Mais vous ne pouvez pas déréférencer l’itérateur retourné par `end()`.  
  
 Notez que vous ne pouvez pas faire référence à un élément de liste directement étant donné sa position numérique--nécessitant un itérateur à accès aléatoire. Par conséquent, une liste est *pas* utilisable en tant que conteneur pour la classe de modèle sous-jacent [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Un itérateur de liste stocke un handle vers son nœud liste associée, qui à son tour stocke un handle à son conteneur associé. Vous pouvez utiliser des itérateurs uniquement avec leurs objets conteneur associé. Un itérateur de liste reste valide tant que son nœud liste associée est associé à une liste. En outre, un itérateur valide est déréférençable : vous pouvez l’utiliser pour accéder ou de modifier la valeur de l’élément qu’il désigne--tant qu’il n’est pas égal à `end()`.  
  
 Effacer ou de suppression d’un élément appelle le destructeur pour sa valeur stockée. Détruire le conteneur efface tous les éléments. Par conséquent, un conteneur dont le type élément est une classe ref garantit qu’aucun élément ne survivre le conteneur. Notez, toutefois, qu’un conteneur de handles ne *pas* détruire ses éléments.  
  
## <a name="members"></a>Membres

## <a name="assign"></a> List::Assign (STL/CLR)
Remplace tous les éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *count*  
 Nombre d’éléments à insérer.  
  
 *first*  
 Début de la plage à insérer.  
  
 *last*  
 Fin de la plage à insérer.  
  
 *right*  
 Énumération à insérer.  
  
 *Val*  
 Valeur de l’élément à insérer.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre remplace la séquence contrôlée par une répétition de *nombre* éléments ayant la valeur *val*. Vous utilisez pour remplir le conteneur avec des éléments dont la même valeur.  
  
 Si `InIt` est de type entier, la deuxième fonction membre comporte comme `assign((size_type)first, (value_type)last)`. Sinon, elle remplace la séquence contrôlée par la séquence [`first`, `last`). Utilisez-la pour rendre le contrôlée une copie de la séquence une autre séquence.  
  
 La troisième fonction membre remplace la séquence contrôlée par la séquence désignée par l’énumérateur *droit*. Il permet d’effectuer la séquence contrôlée une copie d’une séquence décrite par un énumérateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_assign.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    cliext::list<wchar_t>::iterator it = c1.end();   
    c2.assign(c1.begin(), --it);   
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
 
## <a name="back"></a> List::Back (STL/CLR)
Accède au dernier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reference back();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne une référence au dernier élément de la séquence contrôlée, qui doit être non vide. Vous l’utilisez pour accéder au dernier élément, lorsque vous savez qu’il existe.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="back_item"></a> List::back_item (STL/CLR)
Accède au dernier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property value_type back_item;  
```  
  
### <a name="remarks"></a>Notes  
 La propriété accède le dernier élément de la séquence contrôlée, qui doit être non vide. Vous l’utilisez pour lire ou écrire le dernier élément lorsque vous savez qu’il existe.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_back_item.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="begin"></a> List::Begin (STL/CLR)
Désigne le début de la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur à accès aléatoire qui désigne le premier élément de la séquence contrôlée, ou juste après la fin d’une séquence vide. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` début de la séquence contrôlée, mais son état peut changer si la longueur de la séquence contrôlée change.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_begin.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::list<wchar_t>::iterator it = c1.begin();   
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

## <a name="clear"></a> List::Clear (STL/CLR)
Supprime tous les éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void clear();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre appelle [list::erase (STL/CLR)](../dotnet/list-erase-stl-clr.md) `(` [list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md) `(),` [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md) `())`. Vous l’utilisez pour vous assurer que la séquence contrôlée est vide.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_clear.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="const_iterator"></a> List::const_iterator (STL/CLR)
Type d'un itérateur constant pour la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type non spécifié `T2` qui peut servir d’itérateur à accès aléatoire constant pour la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_const_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> List::const_reference (STL/CLR)
Type d'une référence constante à un élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit une référence constante à un élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_const_reference.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        cliext::list<wchar_t>::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> List::const_reverse_iterator (STL/CLR)
Le type d’un itérateur inverse constant pour la séquence contrôlée...  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type non spécifié `T4` qui peut servir d’itérateur inverse constant pour la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="difference_type"></a> List::difference_type (STL/CLR)
Les types d’une distance signée entre deux éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un nombre d’éléments signés.  
  
### <a name="example"></a>Exemple  
  
```cpp 
// cliext_list_difference_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::list<wchar_t>::difference_type diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it) ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.end();   
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

## <a name="empty"></a> List::Empty (STL/CLR)
Vérifie l'absence d'éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la valeur true pour une séquence contrôlée vide. Il est équivalent à [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)`() == 0`. Vous l’utilisez pour tester si la liste est vide.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_empty.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="end"></a> List::end (STL/CLR)
Désigne la fin de la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur à accès aléatoire qui pointe juste après la fin de la séquence contrôlée. Vous l’utilisez pour obtenir un itérateur qui désigne la fin de la séquence contrôlée ; son état ne change pas si la longueur de la séquence contrôlée change.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_end.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::list<wchar_t>::iterator it = c1.end();   
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

## <a name="erase"></a> List::Erase (STL/CLR)
Supprime les éléments placés aux positions spécifiées.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *first*  
 Début de la plage à effacer.  
  
 *last*  
 Fin de la plage à effacer.  
  
 *where*  
 Élément à effacer.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre supprime l’élément de la séquence contrôlée vers lequel pointé *où*. Il permet de supprimer un élément unique.  
  
 La deuxième fonction membre supprime l’élément de la séquence contrôlée dans la plage [`first`, `last`). Il permet de supprimer de zéro ou plusieurs éléments contigus.  
  
 Les deux fonctions membres retournent un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md) `()` si cet élément n’existe.  
  
 Lorsque vous supprimez des éléments, le nombre de copies de l’élément est linéaire quant au nombre d’éléments entre la fin de l’effacement et la fin la plus proche de la séquence. (Lorsque vous supprimez un ou plusieurs éléments à chaque extrémité de la séquence, aucune copie de l’élément se produire.)  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_erase.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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
    cliext::list<wchar_t>::iterator it = c1.end();   
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

## <a name="front"></a> List::Front (STL/CLR)
Accède au premier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reference front();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne une référence au premier élément de la séquence contrôlée, qui doit être non vide. Vous l’utilisez pour lire ou écrire le premier élément, lorsque vous savez qu’il existe.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="front_item"></a> List::front_item (STL/CLR)
Accède au premier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property value_type front_item;  
```  
  
### <a name="remarks"></a>Notes  
 La propriété accède au premier élément de la séquence contrôlée, qui doit être non vide. Vous l’utilisez pour lire ou écrire le premier élément, lorsque vous savez qu’il existe.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_front_item.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="generic_container"></a> List::generic_container (STL/CLR)
Le type de l’interface générique pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Microsoft::VisualC::StlClr::  
    IList<generic_value>  
    generic_container;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit l’interface générique pour cette classe de conteneur de modèle.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_generic_container.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
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

## <a name="generic_iterator"></a> List::generic_iterator (STL/CLR)
Le type d’un itérateur pour une utilisation avec l’interface générique pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un itérateur générique qui peut être utilisé avec l’interface générique pour cette classe de conteneur de modèle.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
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

## <a name="generic_reverse_iterator"></a> List::generic_reverse_iterator (STL/CLR)
Le type d’un itérateur inverse pour une utilisation avec l’interface générique pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un itérateur inverse générique qui peut être utilisé avec l’interface générique pour cette classe de conteneur de modèle.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
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

## <a name="generic_value"></a> List::generic_value (STL/CLR)
Le type d’un élément pour une utilisation avec l’interface générique pour le conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stockée pour une utilisation avec l’interface générique pour cette classe de conteneur de modèle.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_generic_value.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
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

## <a name="insert"></a> List::Insert (STL/CLR)
Ajoute des éléments à une position spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *count*  
 Nombre d’éléments à insérer.  
  
 *first*  
 Début de la plage à insérer.  
  
 *last*  
 Fin de la plage à insérer.  
  
 *right*  
 Énumération à insérer.  
  
 *Val*  
 Valeur de l’élément à insérer.  
  
 *where*  
 Emplacement dans le conteneur à insérer avant.  
  
### <a name="remarks"></a>Notes  
 Chacune du membre fonctions insertions, avant l’élément vers lequel pointé *où* dans la séquence contrôlée, une séquence spécifiée par les opérandes restants.  
  
 La première fonction membre insère un élément avec la valeur *val* et retourne un itérateur qui désigne l’élément nouvellement inséré. Il permet d’insérer un élément unique avant un emplacement désigné par un itérateur.  
  
 La deuxième fonction membre insère une répétition de *nombre* éléments ayant la valeur *val*. Il permet d’insérer de zéro ou plusieurs éléments contigus qui sont toutes les copies de la même valeur.  
  
 Si `InIt` est un type entier, la troisième fonction membre se comporte comme `insert(where, (size_type)first, (value_type)last)`. Sinon, elle insère la séquence [`first`, `last`). Il permet d’insérer de zéro ou plusieurs éléments contigus, copié à partir d’une autre séquence.  
  
 La quatrième fonction membre insère la séquence désignée par le *droit*. Il permet d’insérer une séquence décrite par un énumérateur.  
  
 Quand vous insérez un élément unique, le nombre de copies de l’élément est linéaire quant au nombre d’éléments entre le point d’insertion et la fin la plus proche de la séquence. (Lors de l’insertion d’un ou plusieurs éléments à chaque extrémité de la séquence, aucune copie de l’élément se produire.) Si `InIt` est un itérateur d’entrée, la troisième fonction membre exécute efficacement une insertion unique pour chaque élément dans la séquence. Sinon, lors de l’insertion `N` éléments, le nombre de copies de l’élément est linéaire pour `N` plus le nombre d’éléments entre le point d’insertion et la fin la plus proche de la séquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_insert.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::list<wchar_t> c2;   
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
  
// insert a single value using index   
    it = c2.begin();   
    ++it, ++it, ++it;   
    c2.insert(it, L'z');   
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

## <a name="iterator"></a> List::iterator (STL/CLR)
Type d'un itérateur pour la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type non spécifié `T1` qui peut servir d’itérateur à accès aléatoire pour la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::iterator it = c1.begin();   
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

## <a name="list"></a> List::List (STL/CLR)
Construit un objet conteneur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
list();  
list(list<Value>% right);  
list(list<Value>^ right);  
explicit list(size_type count);  
list(size_type count, value_type val);  
template<typename InIt>  
    list(InIt first, InIt last);  
list(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *count*  
 Nombre d’éléments à insérer.  
  
 *first*  
 Début de la plage à insérer.  
  
 *last*  
 Fin de la plage à insérer.  
  
 *right*  
 Objet ou plage à insérer.  
  
 *Val*  
 Valeur de l’élément à insérer.  
  
### <a name="remarks"></a>Notes  
  
 Le constructeur :  
  
 `list();`  
  
 Initialise la séquence contrôlée sans éléments. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide.  
  
 Le constructeur :  
  
 `list(list<Value>% right);`  
  
 Initialise la séquence contrôlée par la séquence [`right.begin()`, `right.end()`). Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de liste *droit*.  
  
 Le constructeur :  
  
 `list(list<Value>^ right);`  
  
 Initialise la séquence contrôlée par la séquence [`right->begin()`, `right->end()`). Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de liste dont le handle est *droit*.  
  
 Le constructeur :  
  
 `explicit list(size_type count);`  
  
 Initialise la séquence contrôlée avec *nombre* éléments dont la valeur `value_type()`. Vous utilisez pour remplir le conteneur avec des éléments dont la valeur par défaut.  
  
 Le constructeur :  
  
 `list(size_type count, value_type val);`  
  
 Initialise la séquence contrôlée avec *nombre* éléments dont la valeur *val*. Vous utilisez pour remplir le conteneur avec des éléments dont la même valeur.  
  
 Le constructeur :  
  
 `template<typename InIt>`  
  
 `list(InIt first, InIt last);`  
  
 Initialise la séquence contrôlée par la séquence [`first`, `last`). Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence.  
  
 Le constructeur :  
  
 `list(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Initialise la séquence contrôlée par la séquence désignée par l’énumérateur *droit*. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_construct.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::list<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::list<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::list<wchar_t>::iterator it = c3.end();   
    cliext::list<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::list<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::list<wchar_t> c8(%c3);   
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

## <a name="merge"></a> List::Merge (STL/CLR)
Fusionne deux séquences contrôlées ordonnées.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void merge(list<Value>% right);  
template<typename Pred2>  
    void merge(list<Value>% right, Pred2 pred);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Pred*  
 Comparateur pour les paires d’éléments.  
  
 *right*  
 Conteneur à fusionner.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre supprime tous les éléments de la séquence contrôlée par *droit* et les insérer dans la séquence contrôlée. Les deux séquences doivent être triées précédemment par `operator<` --éléments ne doivent pas diminution de valeur que vous progressez dans une séquence. La séquence résultante est également ordonnée par `operator<`. Vous utilisez cette fonction membre pour fusionner deux séquences augmentent la valeur dans une séquence qui augmente également dans valeur.  
  
 La deuxième fonction membre comporte comme la première, sauf que les séquences sont classés par `pred`  --  `pred(X, Y)` doit avoir la valeur false pour tout élément `X` qui suit l’élément `Y` dans la séquence. Vous l’utilisez pour fusionner deux séquences sont classés par une fonction de prédicat ou un délégué que vous spécifiez.  
  
 Les fonctions permettent d’effectuer une fusion stable--aucune paire d’éléments dans une des séquences contrôlées d’origine n’est inversée dans la séquence contrôlée obtenue. En outre, si une paire d’éléments `X` et `Y` dans la séquence contrôlée obtenue a un classement équivalent-- `!(X < Y) && !(X < Y)` --un élément de la séquence contrôlée d’origine apparaît avant un élément à partir de la séquence contrôlée par *droit*.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_merge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
typedef cliext::list<wchar_t> Mylist;   
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'c');   
    c1.push_back(L'e');   
  
// display initial contents " a c e"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    cliext::list<wchar_t> c2;   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
    c2.push_back(L'f');   
  
// display initial contents " b d f"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// merge and display   
    cliext::list<wchar_t> c3(c1);   
    c3.merge(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
  
// sort descending, merge descending, and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.merge(c1, cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 a c e  
 b d f  
 a b c d e f  
c2.size() = 0  
 e c a  
 f e d c b a  
 f e e d c c b a a  
c1.size() = 0  
```  

## <a name="op_as"></a> List::operator = (STL/CLR)
Remplace la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
list<Value>% operator=(list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *right*  
 Conteneur à copier.  
  
### <a name="remarks"></a>Notes  
 Les copies d’opérateur membre *droit* à l’objet, puis retourne `*this`. Utilisez-le pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans *droit*.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_operator_as.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="pop_back"></a> List::pop_back (STL/CLR)
Supprime le dernier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void pop_back();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre supprime le dernier élément de la séquence contrôlée, qui doit être non vide. Il permet de raccourcir la liste d’un élément à l’arrière.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_pop_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="pop_front"></a> List::pop_front (STL/CLR)
Supprime le premier élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void pop_front();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre supprime le premier élément de la séquence contrôlée, qui doit être non vide. Il permet de raccourcir la liste d’un élément au début.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_pop_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_front();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
b c  
```  

## <a name="push_back"></a> List::push_back (STL/CLR)
Ajoute un nouvel élément dernière.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void push_back(value_type val);  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre insère un élément avec la valeur `val` à la fin de la séquence contrôlée. Il permet d’ajouter un autre élément à la liste.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_push_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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
  
## <a name="push_front"></a> List::push_front (STL/CLR)
Ajoute un nouvel élément de premier.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void push_front(value_type val);  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre insère un élément avec la valeur `val` au début de la séquence contrôlée. Il permet d’ajouter un autre élément à la liste.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_push_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_front(L'a');   
    c1.push_front(L'b');   
    c1.push_front(L'c');   
  
// display contents " c b a"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="rbegin"></a> List::rbegin (STL/CLR)
Désigne le début de la séquence contrôlée inverse.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur inverse qui désigne le dernier élément de la séquence contrôlée, ou juste après le début d’une séquence vide. Par conséquent, il désigne le `beginning` de la séquence inverse. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` début de la séquence contrôlée vue dans l’ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_rbegin.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();   
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

## <a name="reference"></a> List::Reference (STL/CLR)
Type d'une référence à un élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit une référence à un élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_reference.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::list<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::list<wchar_t>::reference ref = *it;   
  
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

## <a name="remove"></a> List::Remove (STL/CLR)
Supprime un élément avec une valeur spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void remove(value_type val);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Val*  
 Valeur de l’élément à supprimer.  
  
### <a name="remarks"></a>Notes  
 La fonction membre supprime un élément dans la séquence contrôlée pour laquelle `((System::Object^)val)->Equals((System::Object^)x)` a la valeur true (le cas échéant). Il permet d’effacer un élément arbitraire avec la valeur spécifiée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_remove.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove(L'A');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();  
  
// remove and redisplay   
    c1.remove(L'b');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a c  
```  

## <a name="remove_if"></a> List::remove_if (STL/CLR)
Supprime les éléments qui réussissent un test spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Pred1>  
    void remove_if(Pred1 pred);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Pred*  
 Test pour les éléments à supprimer.  
  
### <a name="remarks"></a>Notes  
 La fonction membre supprime de la séquence contrôlée (efface) chaque élément `X` pour laquelle `pred(X)` a la valeur true. Il permet de supprimer tous les éléments qui satisfont à une condition que vous spécifiez comme une fonction ou un délégué.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_remove_if.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b b b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(   
        cliext::equal_to<wchar_t>(), L'd'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(   
        cliext::not_equal_to<wchar_t>(), L'b'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b b b c  
a b b b c  
b b b  
``` 

## <a name="rend"></a> List::rend (STL/CLR)
Désigne la fin de la séquence contrôlée inverse.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur inverse qui pointe juste après le début de la séquence contrôlée. Par conséquent, il désigne le `end` de la séquence inverse. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` fin de la séquence contrôlée vue dans l’ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_rend.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();   
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

## <a name="resize"></a> List::Resize (STL/CLR)
Modifie le nombre d’éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *NEW_SIZE*  
 Nouvelle taille de la séquence contrôlée.  
  
 *Val*  
 Valeur de l’élément de remplissage.  
  
### <a name="remarks"></a>Notes  
 Les deux fonctions membres Vérifiez que [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()` retourne désormais *new_size*. Si elle doit rallonger la séquence contrôlée, la première fonction membre ajoute des éléments avec la valeur `value_type()`, tandis que la deuxième fonction membre ajoute des éléments avec la valeur *val*. Pour rendre la séquence contrôlée, les deux fonctions membres effacement efficacement le dernier élément [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size` fois. Vous l’utilisez pour vous assurer que la séquence contrôlée a taille *new_size*, par la suppression ou de la séquence contrôlée en cours de remplissage.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_resize.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::list<wchar_t> c1;   
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

## <a name="reverse"></a> List::Reverse (STL/CLR)
Inverse la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void reverse();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre inverse l’ordre de tous les éléments dans la séquence contrôlée. Vous l’utilisez pour refléter une liste d’éléments.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_reverse.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// reverse and redisplay   
    c1.reverse();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
c b a  
```  

## <a name="reverse_iterator"></a> List::reverse_iterator (STL/CLR)
Type d'un itérateur inverse pour la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type non spécifié `T3` qui peut servir d’itérateur inverse pour la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();   
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
  
## <a name="size"></a> List::Size (STL/CLR)
Compte le nombre d'éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la longueur de la séquence contrôlée. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si vous intéresse est si la séquence a une taille différente de zéro, consultez [list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_size.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="size_type"></a> List::size_type (STL/CLR)
Le type d’une distance signée entre deux éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un nombre d’éléments de non négatif.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_size_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::list<wchar_t>::size_type diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```

## <a name="sort"></a> List::sort (STL/CLR)
Ordonne la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Pred*  
 Comparateur pour les paires d’éléments.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre réorganise les éléments dans la séquence contrôlée afin qu’ils sont classés par `operator<` --éléments ne réduisez pas de valeur au cours de la séquence. Vous utilisez cette fonction membre pour trier la séquence dans l’ordre croissant.  
  
 La deuxième fonction membre comporte comme la première, sauf que la séquence est ordonnée par `pred`  --  `pred(X, Y)` a la valeur false pour tout élément `X` qui suit l’élément `Y` dans la séquence résultante. Vous l’utilisez pour trier la séquence dans un ordre que vous spécifiez par une fonction de prédicat ou un délégué.  
  
 Les fonctions permettent d’effectuer un tri stable--aucune paire d’éléments dans la séquence contrôlée d’origine n’est inversée dans la séquence contrôlée obtenue.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_sort.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
c b a  
a b c  
``` 

## <a name="splice"></a> List::splice (STL/CLR)
Restitch les liens entre les nœuds.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *first*  
 Début de la plage d’effectuer l’opération splice.  
  
 *last*  
 Fin de la plage d’effectuer l’opération splice.  
  
 *right*  
 Conteneur à splice à partir de.  
  
 *where*  
 Emplacement dans le conteneur d’effectuer l’opération splice avant.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre insère la séquence contrôlée par *droit* avant l’élément dans la séquence contrôlée vers lequel pointe *où*. Elle supprime également tous les éléments de *droit*. (`%right` ne doit pas correspondre `this`.) Il permet de splice toutes une seule liste dans un autre.  
  
 La deuxième fonction membre supprime l’élément vers lequel pointé *première* dans la séquence contrôlée par *droit* et l’insère avant l’élément dans la séquence contrôlée vers lequel pointe *où* . (Si `where` `==` `first` `||` `where` `== ++first`, aucune modification n’intervient.) Vous l’utilisez pour ajouter un élément unique d’une liste dans un autre.  
  
 La troisième fonction membre insère la sous-plage désignée par [`first`, `last`) à partir de la séquence contrôlée par *droit* avant l’élément dans la séquence contrôlée vers lequel pointée *où*. Elle supprime également la sous-plage d’origine à partir de la séquence contrôlée par *droit*. (If `right` `==` `this`, la plage [`first`, `last`) ne doit pas inclure l’élément désigné par *où*.) Il permet de splice une sous-séquence de zéro ou plusieurs éléments d’une liste dans un autre.  
  
### <a name="example"></a>Exemple  
  
```cpp
// cliext_list_splice.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
c1.size() = 0  
 a b c  
 a  
 b c  
 b c a  
c2.size() = 0  
```    

## <a name="swap"></a> List::swap (STL/CLR)
Échange le contenu de deux conteneurs.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void swap(list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *right*  
 Conteneur avec lequel échanger le contenu.  
  
### <a name="remarks"></a>Notes  
 La fonction membre échange les séquences contrôlées entre `*this` et *droit*. Elle le fait en temps constant et ne lève aucune exception. Vous l’utilisez comme un moyen rapide pour échanger le contenu de deux conteneurs.  
  
### <a name="example"></a>Exemple  
  
```cpp 
// cliext_list_swap.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::list<wchar_t> c2(5, L'x');   
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

## <a name="to_array"></a> List::to_array (STL/CLR)
Copie la séquence contrôlée vers un nouveau tableau.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un tableau contenant la séquence contrôlée. Vous l’utilisez pour obtenir une copie de la séquence contrôlée sous forme de tableau.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_to_array.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="unique"></a> List::unique (STL/CLR)
Supprime des éléments adjacents qui réussissent un test spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Pred*  
 Comparateur pour les paires d’éléments.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre supprime de la séquence contrôlée (efface) chaque élément dont la valeur est égale à son élément précédent--si élément `X` précède l’élément `Y` et `X == Y`, la fonction membre supprime `Y`. Vous utilisez pour supprimer tous sauf un copie de chaque sous-séquence des éléments adjacents qui égal de comparaison. Notez que si la séquence contrôlée est triée, par exemple en appelant [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`, la fonction membre laisse uniquement les éléments avec des valeurs uniques. (D’où leur nom.)  
  
 La deuxième fonction membre comporte comme la première, sauf qu’elle supprime chaque élément `Y` suivant un élément `X` pour lequel `pred(X, Y)`. Il permet de supprimer tous sauf un copie de chaque sous-séquence des éléments adjacents qui satisfont une fonction de prédicat ou un délégué que vous spécifiez. Notez que si la séquence contrôlée est triée, par exemple en appelant `sort(pred)`, la fonction membre laisse uniquement les éléments qui n’ont pas un classement équivalent à tous les autres éléments.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a a b c  
a b c  
a a  
```  

## <a name="value_type"></a> List::Value_type (STL/CLR)
Type d’un élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle *valeur*.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_value_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::list<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
``` 

## <a name="op_neq"></a> opérateur ! = (liste) (STL/CLR)
Liste différent de comparaison.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value>  
    bool operator!=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *left*  
 Conteneur de gauche à comparer.  
  
 *right*  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(left == right)`. Il permet de tester si *gauche* n’est pas ordonné identique *droit* lorsque les deux listes sont comparées d’élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_operator_ne.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="op_lt"></a> opérateur&lt; (liste) (STL/CLR)
Liste inférieur comparaison.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value>  
    bool operator<(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *left*  
 Conteneur de gauche à comparer.  
  
 *right*  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 L’opérateur fonction retourne true si, pour la position la plus basse `i` pour lequel `!(right[i] < left[i])` il est également vrai que `left[i] < right[i]`. Sinon, elle retourne `left->size() < right->size()` vous l’utiliser pour tester si *gauche* est classé avant *droit* lorsque les deux listes sont comparées d’élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_operator_lt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="op_lteq"></a> opérateur&lt;= (liste) (STL/CLR)
Liste inférieure ou égale comparaison.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value>  
    bool operator<=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *left*  
 Conteneur de gauche à comparer.  
  
 *right*  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(right < left)`. Il permet de tester si *gauche* n’est pas ordonné après *droit* lorsque les deux listes sont comparées d’élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_operator_le.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="op_eq"></a> opérateur == (liste) (STL/CLR)
Liste de comparaison égale.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp 
template<typename Value>  
    bool operator==(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *left*  
 Conteneur de gauche à comparer.  
  
 *right*  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne true uniquement si les séquences contrôlées par *gauche* et *droit* ont la même longueur et, pour chaque position `i`, `left[i] ==` `right[i]`. Il permet de tester si *gauche* est ordonné identique *droit* lorsque les deux listes sont comparées d’élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_operator_eq.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="op_gt"></a> opérateur&gt; (liste) (STL/CLR)
Comparaison de supériorité de la liste.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value>  
    bool operator>(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *left*  
 Conteneur de gauche à comparer.  
  
 *right*  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `right` `<` `left`. Il permet de tester si *gauche* est trié après *droit* lorsque les deux listes sont comparées d’élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_operator_gt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="op_gteq"></a> opérateur&gt;= (liste) (STL/CLR)
Liste supérieur ou égal à comparaison.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value>  
    bool operator>=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *left*  
 Conteneur de gauche à comparer.  
  
 *right*  
 Conteneur de droite à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(left` `<` `right)`. Il permet de tester si *gauche* n’est pas classé avant *droit* lorsque les deux listes sont comparées d’élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_operator_ge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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