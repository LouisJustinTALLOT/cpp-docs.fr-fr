---
title: adaptateur (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter
- cliext::collection_adapter::collection_adapter
- cliext::collection_adapter::difference_type
- cliext::collection_adapter::end
- cliext::collection_adapter::iterator
- cliext::collection_adapter::key_type
- cliext::collection_adapter::mapped_type
- cliext::collection_adapter::operator=
- cliext::collection_adapter::reference
- cliext::collection_adapter::size
- cliext::collection_adapter::size_type
- cliext::collection_adapter::swap
- cliext::collection_adapter::value_type
- cliext::make_collection
- cliext::range_adapter
- cliext::operator=
- cliext::range_adapter::operator=
- cliext::range_adapter::range_adapter
dev_langs:
- C++
helpviewer_keywords:
- <adapter> header [STL/CLR]
- adapter [STL/CLR]
- <cliext/adapter> header [STL/CLR]
- collection_adapter class [STL/CLR]
- base member [STL/CLR]
- begin member [STL/CLR]
- collection_adapter member [STL/CLR]
- difference_type member [STL/CLR]
- end member [STL/CLR]
- iterator member [STL/CLR]
- key_type member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- value_type member [STL/CLR]
- make_collection function [STL/CLR]
- range_adapter class [STL/CLR]
- operator= member [STL/CLR]
- range_adapter member [STL/CLR]
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7023ef21258a5b93d889d02c1b586b524c8b98be
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42573122"
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)
L’en-tête STL/CLR `<cliext/adapter>` spécifie deux classes de modèle (`collection_adapter` et `range_adapter`) et la fonction de modèle `make_collection`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#include <cliext/adapter>  
```  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<cliext/adaptateur >  
  
 **Namespace :** cliext 
  
## <a name="declarations"></a>Déclarations  
  
|Classe|Description|  
|-----------|-----------------|  
|[collection_adapter (STL/CLR)](#collection_adapter)|Encapsule la collection de la bibliothèque de classes de Base (BCL) sous forme de plage.|  
|[range_adapter (STL/CLR)](#range_adapter)|Encapsule la plage comme une collection de la BCL.|  

|Fonction|Description|  
|--------------|-----------------|  
|[make_collection (STL/CLR)](#make_collection)|Crée une carte de la plage à l’aide d’une paire d’itérateurs.|   
  
## <a name="members"></a>Membres

## <a name="collection_adapter"></a> collection_adapter (STL/CLR)
Encapsule une collection .NET à utiliser comme un conteneur STL/CLR. Un `collection_adapter` est une classe de modèle qui décrit un objet de conteneur STL/CLR simple. Encapsule une interface de bibliothèque de classes de Base (BCL), elle retourne une paire d’itérateurs qui vous permet de manipuler la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Coll*  
 Le type de la collection encapsulée.  
  
### <a name="specializations"></a>Spécialisations  
  
|Spécialisation|Description|  
|--------------------|-----------------|  
|IEnumerable|Séquences dans les éléments.|  
|ICollection|Gère un groupe d’éléments.|  
|IList|Gère un groupe ordonné d’éléments.|  
|IDictionary|Conserver un ensemble de {clé, valeur} paires.|  
|IEnumerable\<valeur >|Séquences par le biais des éléments typés.|  
|ICollection\<valeur >|Gère un groupe d’éléments typés.|  
|IList\<valeur >|Gère un groupe ordonné d’éléments typés.|  
|IDictionary\<valeur >|Gère un ensemble de typé {clé, valeur} paires.|  
  
### <a name="members"></a>Membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[collection_adapter::difference_type (STL/CLR)](#difference_type)|Type d'une distance signée entre deux éléments.|  
|[collection_adapter::iterator (STL/CLR)](#iterator)|Type d'un itérateur pour la séquence contrôlée.|  
|[collection_adapter::key_type (STL/CLR)](#key_type)|Le type d’une clé de dictionnaire.|  
|[collection_adapter::mapped_type (STL/CLR)](#mapped_type)|Le type d’une valeur de dictionnaire.|  
|[collection_adapter::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|  
|[collection_adapter::size_type (STL/CLR)](#size_type)|Type d'une distance signée entre deux éléments.|  
|[collection_adapter::value_type (STL/CLR)](#value_type)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[collection_adapter::base (STL/CLR)](#base)|Désigne l’interface encapsulée de la BCL.|  
|[collection_adapter::begin (STL/CLR)](#begin)|Désigne le début de la séquence contrôlée.|  
|[collection_adapter::collection_adapter (STL/CLR)](#collection_adapter_collection_adapter)|Construit un objet d’adaptateur.|  
|[collection_adapter::end (STL/CLR)](#end)|Désigne la fin de la séquence contrôlée.|  
|[collection_adapter::size (STL/CLR)](#size)|Compte le nombre d'éléments.|  
|[collection_adapter::swap (STL/CLR)](#swap)|Échange le contenu de deux conteneurs.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[collection_adapter::operator= (STL/CLR)](#op_eq)|Remplace le descripteur stocké de la BCL.|  
  
### <a name="remarks"></a>Notes  
 Vous utilisez cette classe de modèle pour manipuler un conteneur BCL comme un conteneur STL/CLR. La `collection_adapter` stocke un handle vers une interface BCL, qui à son tour contrôle une séquence d’éléments. Un `collection_adapter` objet `X` retourne une paire d’itérateurs d’entrée `X.begin()` et `X.end()` que vous utilisez pour consulter les éléments, dans l’ordre. Certaines des spécialisations vous permettent également d’écrire `X.size()` pour déterminer la longueur de la séquence contrôlée.  

## <a name="base"></a> collection_adapter::base (STL/CLR)
Désigne l’interface encapsulée de la BCL.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Coll^ base();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le handle d’interface BCL stocké.  
  
### <a name="example"></a>Exemple  
  
```cpp
// cliext_collection_adapter_base.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);   
    return (0);   
    }  
```  
  
```Output  
 x x x x x x  
base() same = True  
```  

## <a name="begin"></a> collection_adapter::Begin (STL/CLR)
Désigne le début de la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur d’entrée qui désigne le premier élément de la séquence contrôlée, ou juste après la fin d’une séquence vide.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_collection_adapter_begin.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mycoll::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  

## <a name="collection_adapter_collection_adapter"></a> collection_adapter::collection_adapter (STL/CLR)
Construit un objet d’adaptateur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
collection_adapter();  
collection_adapter(collection_adapter<Coll>% right);  
collection_adapter(collection_adapter<Coll>^ right);  
collection_adapter(Coll^ collection);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *collection*  
 Handle de la BCL à encapsuler.  
  
 *right*  
 Objet à copier.  
  
### <a name="remarks"></a>Notes  
 Le constructeur :  
  
 `collection_adapter();`  
  
 Initialise le handle stocké avec `nullptr`.  
  
 Le constructeur :  
  
 `collection_adapter(collection_adapter<Coll>% right);`  
  
 Initialise le handle stocké avec `right.` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 Le constructeur :  
  
 `collection_adapter(collection_adapter<Coll>^ right);`  
  
 Initialise le handle stocké avec `right->` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 Le constructeur :  
  
 `collection_adapter(Coll^ collection);`  
  
 Initialise le handle stocké avec `collection`.  
  
### <a name="example"></a>Exemple  
  
```cpp 
// cliext_collection_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
  
// construct an empty container   
    Mycoll c1;   
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);   
  
// construct with a handle   
    Mycoll c2(%d6x);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mycoll c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mycoll c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
```  
  
```Output  
base() null = True  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  

## <a name="difference_type"></a> collection_adapter::difference_type (STL/CLR)
Les types d’une distance signée entre deux éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un nombre d’éléments signés.  
  
### <a name="example"></a>Exemple  
  
```cpp 
// cliext_collection_adapter_difference_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mycoll::difference_type diff = 0;   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  

## <a name="end"></a> collection_adapter::end (STL/CLR)
Désigne la fin de la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur d’entrée qui pointe juste après la fin de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp 
// cliext_collection_adapter_end.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="iterator"></a> collection_adapter::iterator (STL/CLR)
Type d'un itérateur pour la séquence contrôlée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet de type non spécifié `T1` qui peut servir d’itérateur d’entrée pour la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_collection_adapter_iterator.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="key_type"></a> collection_adapter::KEY_TYPE (STL/CLR)
Le type d’une clé de dictionnaire.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Key`, dans une spécialisation pour `IDictionary` ou `IDictionary<Value>`; sinon, il n’est pas défini.  
  
### <a name="example"></a>Exemple  
  
```cpp
// cliext_collection_adapter_key_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="mapped_type"></a> collection_adapter::mapped_type (STL/CLR)
Le type d’une valeur de dictionnaire.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Value mapped_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Value`, dans une spécialisation pour `IDictionary` ou `IDictionary<Value>`; sinon, il n’est pas défini.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_collection_adapter_mapped_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="op_eq"></a> collection_adapter::operator = (STL/CLR)
Remplace le descripteur stocké de la BCL.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *right*  
 Carte à copier.  
  
### <a name="remarks"></a>Notes  
 Les copies d’opérateur membre *droit* à l’objet, puis retourne `*this`. Utilisez-le pour remplacer le handle BCL stocké par une copie du handle BCL stockée dans *droit*.  
  
### <a name="example"></a>Exemple  
  
```cpp 
// cliext_collection_adapter_operator_as.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mycoll c2;   
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

## <a name="reference"></a> collection_adapter::Reference (STL/CLR)
Type d'une référence à un élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit une référence à un élément.  
  
### <a name="example"></a>Exemple  
  
```cpp 
// cliext_collection_adapter_reference.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Mycoll::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="size"></a> collection_adapter::Size (STL/CLR)
Compte le nombre d'éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la longueur de la séquence contrôlée. Il n’est pas défini dans une spécialisation pour `IEnumerable` ou `IEnumerable<Value>`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_collection_adapter_size.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 x x x x x x  
size() = 6  
```  

## <a name="size_type"></a> collection_adapter::size_type (STL/CLR)
Le type d’une distance signée entre deux éléments.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un nombre d’éléments de non négatif.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_collection_adapter_size_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    Mycoll::size_type size = c1.size();   
    System::Console::WriteLine("size() = {0}", size);   
    return (0);   
    }  
```  
  
```Output  
 x x x x x x  
size() = 6  
```  

## <a name="swap"></a> collection_adapter::swap (STL/CLR)
Échange le contenu de deux conteneurs.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void swap(collection_adapter<Coll>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *right*  
 Conteneur avec lequel échanger le contenu.  
  
### <a name="remarks"></a>Notes  
 La fonction membre échange les handles BCL stockées entre `*this` et *droit*.  
  
### <a name="example"></a>Exemple  
  
```cpp
// cliext_collection_adapter_swap.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::deque<wchar_t> d2(5, L'x');   
    Mycoll c2(%d2);   
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

## <a name="value_type"></a> collection_adapter::Value_type (STL/CLR)
Type d’un élément.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle *valeur*, s’il est présent dans la spécialisation ; sinon, il est un synonyme de `System::Object^`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_collection_adapter_value_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display contents " a b c" using value_type   
    for (Mycoll::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mycoll::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="make_collection"></a> make_collection (STL/CLR)
Rendre un `range_adapter` à partir d’une paire d’itérateurs.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Iter>  
    range_adapter<Iter> make_collection(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Iter*  
 Le type des itérateurs encapsulées.  
  
 *first*  
 Premier itérateur à encapsuler.  
  
 *last*  
 Deuxième itérateur à encapsuler.  
  
### <a name="remarks"></a>Notes  
 La fonction de modèle retourne `gcnew range_adapter<Iter>(first, last)`. Utilisez-la pour construire un `range_adapter<Iter>` objet à partir d’une paire d’itérateurs.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_make_collection.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in d1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Collections::ICollection^ p1 =   
        cliext::make_collection(d1.begin(), d1.end());   
    System::Console::WriteLine("Count = {0}", p1->Count);   
    System::Console::WriteLine("IsSynchronized = {0}",   
        p1->IsSynchronized);   
    System::Console::WriteLine("SyncRoot not nullptr = {0}",   
        p1->SyncRoot != nullptr);   
  
// copy the sequence   
    cli::array<System::Object^>^ a1 = gcnew cli::array<System::Object^>(5);   
  
    a1[0] = L'|';   
    p1->CopyTo(a1, 1);   
    a1[4] = L'|';   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
```  
  
```Output  
 a b c  
Count = 3  
IsSynchronized = False  
SyncRoot not nullptr = True  
 | a b c |  
```  

## <a name="range_adapter"></a> range_adapter (STL/CLR)
Classe de modèle qui encapsule une paire d’itérateurs qui sont utilisées pour implémenter plusieurs interfaces de la bibliothèque de classes de Base (BCL). Le range_adapter vous permet de manipuler une plage STL/CLR comme s’il s’agissait d’une collection de la BCL.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Iter*  
 Le type associé aux itérateurs encapsulées.  
  
### <a name="members"></a>Membres  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](#range_adapter_range_adapter)|Construit un objet d’adaptateur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[range_adapter::operator= (STL/CLR)](#range_adapter_op_eq)|Remplace la paire itérateur stocké.|  
  
### <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.Collections.IEnumerable>|Itère les éléments de la collection.|  
|<xref:System.Collections.ICollection>|Gère un groupe d’éléments.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Itère au sein des éléments typés dans la collection...|  
|<xref:System.Collections.Generic.ICollection%601>|Gère un groupe d’éléments typés.|  
  
### <a name="remarks"></a>Notes  
 La range_adapter stocke une paire d’itérateurs, qui à son tour délimiter une séquence d’éléments. L’objet implémente quatre interfaces BCL qui vous permettent de parcourir les éléments, dans l’ordre. Vous utilisez cette classe de modèle pour manipuler des plages STL/CLR comme conteneurs de la BCL.  

## <a name="range_adapter_op_eq"></a> range_adapter::operator = (STL/CLR)
Remplace la paire itérateur stocké.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
range_adapter<Iter>% operator=(range_adapter<Iter>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *right*  
 Carte à copier.  
  
### <a name="remarks"></a>Notes  
 Les copies d’opérateur membre *droit* à l’objet, puis retourne `*this`. Utilisez-le pour remplacer la paire itérateur stocké par une copie de la paire itérateur stocké dans *droit*.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_range_adapter_operator_as.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Myrange c1(d1.begin(), d1.end());   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myrange c2;   
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

## <a name="range_adapter_range_adapter"></a> range_adapter::range_adapter (STL/CLR)
Construit un objet d’adaptateur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
range_adapter();  
range_adapter(range_adapter<Iter>% right);  
range_adapter(range_adapter<Iter>^ right);  
range_adapter(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *first*  
 Premier itérateur à encapsuler.  
  
 *last*  
 Deuxième itérateur à encapsuler.  
  
 *right*  
 Objet à copier.  
  
### <a name="remarks"></a>Notes  
 Le constructeur :  
  
 `range_adapter();`  
  
 Initialise la paire itérateur stocké avec les itérateurs construits par défaut.  
  
 Le constructeur :  
  
 `range_adapter(range_adapter<Iter>% right);`  
  
 Initialise la paire itérateur stocké en copiant la paire stockée dans *droit*.  
  
 Le constructeur :  
  
 `range_adapter(range_adapter<Iter>^ right);`  
  
 Initialise la paire itérateur stocké en copiant la paire stockée dans `*right`.  
  
 Le constructeur :  
  
 `range_adapter(Iter^ first, last);`  
  
 Initialise la paire itérateur stocké avec *première* et *dernière*.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_range_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// construct an empty adapter   
    Myrange c1;   
  
// construct with an iterator pair   
    Myrange c2(d1.begin(), d1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another adapter   
    Myrange c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying an adapter handle   
    Myrange c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a b c  
```  