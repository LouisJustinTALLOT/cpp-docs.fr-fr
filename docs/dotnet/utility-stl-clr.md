---
title: l’utilitaire (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
dev_langs:
- C++
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fcc97e5037898b3a9c39a6c72ed21b2c19a4c777
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36306019"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)
Incluez l’en-tête STL/CLR `<cliext/utility>` pour définir la classe de modèle `pair` et plusieurs fonctions de modèle de prise en charge.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <utility>  
```

## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<cliext/utilitaire >  
  
 **Namespace :** cliext  
  
## <a name="declarations"></a>Déclarations  
  
|Classe|Description|  
|-----------|-----------------|  
|[pair (STL/CLR)](#pair)|Encapsuler une paire d’éléments.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[operator== (pair) (STL/CLR)](#op_eq)|Comparaison égale de la paire.|  
|[operator!= (pair) (STL/CLR)](#op_neq)|Paires de comparaison n’est pas égal.|  
|[operator< (pair) (STL/CLR)](#op_lt)|Paire de comparaison inférieur.|  
|[opérateur\<= (paire) (STL/CLR)](#op_lteq)|Inférieur ou égal paire comparaison.|  
|[operator> (pair) (STL/CLR)](#op_gt)|Supérieure à la comparaison de la paire.|  
|[operator>= (pair) (STL/CLR)](#op_gteq)|Paire supérieur ou égal comparaison.|  
  
|Fonction|Description|  
|--------------|-----------------|  
|[make_pair (STL/CLR)](#make_pair)|Rendre une paire d’une paire de valeurs.|  

## <a name="members"></a>Membres

##<a name="pair"></a> paire (STL/CLR)
La classe de modèle décrit un objet qui encapsule une paire de valeurs.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### <a name="parameters"></a>Paramètres  
 Value1  
 Le type de la première valeur encapsulée.  
  
 Value2  
 Le type de la deuxième valeur encapsulée.  
  
## <a name="members"></a>Membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[pair::first_type (STL/CLR)](#first_type)|Le type de la première valeur encapsulée.|  
|[pair::second_type (STL/CLR)](#second_type)|Le type de la deuxième valeur encapsulée.|  
  
|Objet membre|Description|  
|-------------------|-----------------|  
|[pair::first (STL/CLR)](#first)|La première valeur stockée.|  
|[pair::second (STL/CLR)](#second)|La deuxième valeur stockée.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[pair::pair (STL/CLR)](#pair_pair)|Construit un objet de la paire.|  
|[pair::swap (STL/CLR)](#swap)|Échange le contenu de deux paires.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[pair::operator= (STL/CLR)](#op_as)|Remplace la paire de valeurs stockée.|  
  
## <a name="remarks"></a>Notes  
 L’objet stocke une paire de valeurs. Cette classe de modèle vous permet de combiner deux valeurs en un seul objet. En outre, l’objet `cliext::pair` (décrite ici) stocke uniquement les types managés ; pour stocker une paire de non managé types utilisent `std::pair`, déclarés dans `<utility>`.  


## <a name="first"></a> pair::First (STL/CLR)
La première valeur encapsulée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
Value1 first;  
```  
  
### <a name="remarks"></a>Notes  
 L’objet stocke la première valeur encapsulée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_first.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  

## <a name="first_type"></a> pair::first_type (STL/CLR)
Le type de la première valeur encapsulée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef Value1 first_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Value1`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_first_type.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  

## <a name="op_as"></a> pair::operator = (STL/CLR)
Remplace la paire de valeurs stockée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Paire à copier.  
  
### <a name="remarks"></a>Notes  
 Les copies d’opérateur de membre `right` à l’objet, puis retourne `*this`. Utilisez-le pour remplacer la paire de valeurs stockée avec une copie de la paire de valeurs dans stockée `right`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_operator_as.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
// assign to a new pair   
    cliext::pair<wchar_t, int> c2;   
    c2 = c1;   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 3]  
```  

## <a name="pair_pair"></a> pair::pair (STL/CLR)
Construit un objet de la paire.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
pair();  
pair(pair<Coll>% right);  
pair(pair<Coll>^ right);  
pair(Value1 val1, Value2 val2);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Paire à stocker.  
  
 val1  
 Première valeur à stocker.  
  
 val2  
 Seconde valeur à stocker.  
  
### <a name="remarks"></a>Notes  
 Le constructeur :  
  
 `pair();`  
  
 Initialise la paire stockée avec des valeurs par défaut construit.  
  
 Le constructeur :  
  
 `pair(pair<Value1, Value2>% right);`  
  
 Initialise la paire stockée avec `right.` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) et `right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).  
  
 `pair(pair<Value1, Value2>^ right);`  
  
 Initialise la paire stockée avec `right->` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) et `right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).  
  
 Le constructeur :  
  
 `pair(Value1 val1, Value2 val2);`  
  
 Initialise la paire stockée avec `val1` et `val2`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_construct.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
// construct an empty container   
    cliext::pair<wchar_t, int> c1;   
    System::Console::WriteLine("[{0}, {1}]",   
        c1.first == L'\0' ? "\\0" : "??", c1.second);   
  
// construct with a pair of values   
    cliext::pair<wchar_t, int> c2(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
// construct by copying another pair   
    cliext::pair<wchar_t, int> c3(c2);   
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);   
  
// construct by copying a pair handle   
    cliext::pair<wchar_t, int> c4(%c3);   
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);   
  
    return (0);   
    }  
  
```  
  
```Output  
[\0, 0]  
[x, 3]  
[x, 3]  
[x, 3]  
```  

## <a name="second"></a> pair::second (STL/CLR)
Le deuxième de valeur encapsulée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
Value2 second;  
```  
  
### <a name="remarks"></a>Notes  
 L’objet stocke la deuxième valeur encapsulée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_second.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  

## <a name="second_type"></a> pair::second_type (STL/CLR)
Le type de la deuxième valeur encapsulée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef Value2 second_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Value2`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_second_type.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```    

## <a name="swap"></a> pair::swap (STL/CLR)
Échange le contenu de deux paires.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void swap(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Paire d’échange de contenu avec.  
  
### <a name="remarks"></a>Notes  
 La fonction membre échange la paire de valeurs entre stockée `*this` et `right`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_swap.cpp   
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

## <a name="make_pair"></a> make_pair (STL/CLR)
Rendre un `pair` à partir d’une paire de valeurs.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Value1`  
 Le type de la première valeur encapsulée.  
  
 `Value2`  
 Le type de la deuxième valeur encapsulée.  
  
 `first`  
 Première valeur à encapsuler.  
  
 `second`  
 Seconde valeur à encapsuler.  
  
### <a name="remarks"></a>Notes  
 La fonction de modèle retourne `pair<Value1, Value2>(first, second)`. Utilisez-la pour construire un `pair<Value1, Value2>` objet à partir d’une paire de valeurs.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_make_pair.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    c1 = cliext::make_pair(L'y', 4);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[y, 4]  
```  

## <a name="op_neq"></a> opérateur ! = (paire) (STL/CLR)
Paires de comparaison n’est pas égal.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator!=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Paire de gauche à comparer.  
  
 droite  
 Paire de droit à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(left == right)`. Il permet de tester si `left` n’est pas ordonné identique `right` lorsque deux paires sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp
// cliext_pair_operator_ne.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] != [x 3] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[x 3] != [x 4] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] != [x 3] is False  
[x 3] != [x 4] is True  
```  
  
## <a name="op_lt"></a> opérateur&lt; (paire) (STL/CLR)
Paire de comparaison inférieur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Paire de gauche à comparer.  
  
 droite  
 Paire de droit à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`. Il permet de tester si `left` est ordonné l’avant `right` lorsque deux paires sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_operator_lt.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] < [x 3] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[x 3] < [x 4] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] < [x 3] is False  
[x 3] < [x 4] is True  
```  

## <a name="op_lteq"></a> opérateur&lt;= (paire) (STL/CLR)
Inférieur ou égal paire comparaison.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Paire de gauche à comparer.  
  
 droite  
 Paire de droit à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(right < left)`. Il permet de tester si `left` n’est pas ordonné après `right` lorsque deux paires sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_operator_le.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] <= [x 3] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] <= [x 3] is True  
[x 4] <= [x 3] is False  
```  
  
## <a name="op_eq"></a> opérateur == (pair) (STL/CLR)
Comparaison égale de la paire.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator==(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Paire de gauche à comparer.  
  
 droite  
 Paire de droit à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `left.first ==` `right.first &&` `left.second ==` `right.second`. Il permet de tester si `left` est ordonné identique `right` lorsque deux paires sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_operator_eq.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] == [x 3] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[x 3] == [x 4] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] == [x 3] is True  
[x 3] == [x 4] is False  
```  

## <a name="op_gt"></a> opérateur&gt; (paire) (STL/CLR)
Supérieure à la comparaison de la paire.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Paire de gauche à comparer.  
  
 droite  
 Paire de droit à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `right` `<` `left`. Il permet de tester si `left` est trié après `right` lorsque deux paires sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_operator_gt.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] > [x 3] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[x 4] > [x 3] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] > [x 3] is False  
[x 4] > [x 3] is True  
```  

## <a name="op_gteq"></a> opérateur&gt;= (paire) (STL/CLR)
Paire supérieur ou égal comparaison.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Paire de gauche à comparer.  
  
 droite  
 Paire de droit à comparer.  
  
### <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(left < right)`. Il permet de tester si `left` n’est pas classé avant `right` lorsque deux paires sont comparé élément par élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_pair_operator_ge.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] >= [x 3] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] >= [x 3] is True  
[x 3] >= [x 4] is False  
```  
