---
title: fonctionnel (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/functional>
- cliext::binary_delegate
- cliext::binary_delegate_noreturn
- cliext::binary_negate
- cliext::bind1st
- cliext::bind2nd
- cliext::binder1st
- cliext::binder2nd
- cliext::divides
- cliext::equal_to
- cliext::greater
- cliext::greater_equal
- cliext::less
- cliext::less_equal
- cliext::logical_and
- cliext::logical_not
- cliext::logical_or
- cliext::minus
- cliext::modulus
- cliext::multiplies
- cliext::negate
- cliext::not_equal_to
- cliext::not1
- cliext::not2
- cliext::plus
- cliext::unary_delegate
- cliext::unary_delegate_noreturn
- cliext::unary_negate
dev_langs:
- C++
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
- binary_delegate function [STL/CLR]
- binary_delegate_noreturn function [STL/CLR]
- binary_negate function [STL/CLR]
- bind1st function [STL/CLR]
- bind2nd function [STL/CLR]
- binder1st function [STL/CLR]
- binder2nd function [STL/CLR]
- divides function [STL/CLR]
- equal_to function [STL/CLR]
- greater function [STL/CLR]
- greater_equal function [STL/CLR]
- less function [STL/CLR]
- less_equal function [STL/CLR]
- logical_and function [STL/CLR]
- logical_not function [STL/CLR]
- logical_or function [STL/CLR]
- minus function [STL/CLR]
- modulus function [STL/CLR]
- multiplies function [STL/CLR]
- negate function [STL/CLR]
- not_equal_to function [STL/CLR]
- not1 function [STL/CLR]
- not2 function [STL/CLR]
- plus function [STL/CLR]
- unary_delegate function [STL/CLR]
- unary_delegate_noreturn function [STL/CLR]
- unary_negate function [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 04596cd043b90d8016cd0f9b1ebfe05a9bf82f72
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305902"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)
Incluez l’en-tête STL/CLR `<cliext/functional>` pour définir l’un nombre de classes de modèle et les fonctions et les délégués de modèle associés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <functional>  
```  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<cliext/fonctionnel >  
  
 **Namespace :** cliext 

## <a name="declarations"></a>Déclarations  
  
|délégué|Description|  
|--------------|-----------------|  
|[binary_delegate (STL/CLR)](#binary_delegate)|Délégué à deux arguments.|  
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|Délégué à deux arguments retournant `void`.|  
|[unary_delegate (STL/CLR)](#unary_delegate)|Délégué à un argument.|  
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|Délégué à un argument retour `void`.|  
  
|Classe|Description|  
|-----------|-----------------|  
|[binary_negate (STL/CLR)](#binary_negate)|Functor pour annuler un functor deux arguments.|  
|[binder1st (STL/CLR)](#binder1st)|Functor pour lier le premier argument à un functor deux arguments.|  
|[binder2nd (STL/CLR)](#binder2nd)|Functor pour lier le deuxième argument à un functor deux arguments.|  
|[divides (STL/CLR)](#divides)|Diviser functor.|  
|[equal_to (STL/CLR)](#equal_to)|Fonction de comparaison égale.|  
|[greater (STL/CLR)](#greater)|Fonction de comparaison supérieure.|  
|[greater_equal (STL/CLR)](#greater_equal)|Fonction de comparaison supérieur ou égal à.|  
|[less (STL/CLR)](#less)|Moins functor de comparaison.|  
|[less_equal (STL/CLR)](#less_equal)|Fonction de comparaison inférieur ou égal à.|  
|[logical_and (STL/CLR)](#logical_and)|Logique AND functor.|  
|[logical_not (STL/CLR)](#logical_not)|Logique pas functor.|  
|[logical_or (STL/CLR)](#logical_or)|Functor de OR logique.|  
|[minus (STL/CLR)](#minus)|Soustraire functor.|  
|[modulus (STL/CLR)](#modulus)|Functor de modulo.|  
|[multiplies (STL/CLR)](#multiplies)|Multipliez functor.|  
|[negate (STL/CLR)](#negate)|Functor pour retourner l’argument de l’opération de négation.|  
|[not_equal_to (STL/CLR)](#not_equal_to)|Fonction de comparaison n’est pas égal.|  
|[plus (STL/CLR)](#plus)|Ajoutez un functor.|  
|[unary_negate (STL/CLR)](#unary_negate)|Functor pour annuler un functor un argument.|  
  
|Fonction|Description|  
|--------------|-----------------|  
|[bind1st (STL/CLR)](#bind1st)|Génère un binder1st pour un argument et un functor.|  
|[bind2nd (STL/CLR)](#bind2nd)|Génère un binder2nd pour un argument et un functor.|  
|[not1 (STL/CLR)](#not1)|Génère un unary_negate pour un functor.|  
|[not2 (STL/CLR)](#not2)|Génère un binary_negate pour un functor.|  
   
## <a name="members"></a>Membres

## <a name="binary_delegate"></a> binary_delegate (STL/CLR)
La classe genereic décrit un délégué à deux arguments. Vous l’utilisez spécifier en termes de ses types d’arguments et de retour d’un délégué.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
generic<typename Arg1,  
    typename Arg2,  
    typename Result>  
    delegate Result binary_delegate(Arg1, Arg2);  
```  
  
#### <a name="parameters"></a>Paramètres  
 arg1  
 Le type du premier argument.  
  
 Arg2  
 Le type du second argument.  
  
 Résultat  
 Type de retour.  
  
### <a name="remarks"></a>Notes  
 Le délégué genereic décrit une fonction de deux arguments.  
  
 Notez que pour :  
  
 `binary_delegate<int, int, int> Fun1;`  
  
 `binary_delegate<int, int, int> Fun2;`  
  
 les types `Fun1` et `Fun2` sont des synonymes, tandis que pour :  
  
 `delegate int Fun1(int, int);`  
  
 `delegate int Fun2(int, int);`  
  
 ils ne sont pas du même type.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_binary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
bool key_compare(wchar_t left, wchar_t right)   
    {   
    return (left < right);   
    }   
  
typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="binary_delegate_noreturn"></a> binary_delegate_noreturn (STL/CLR)
La classe genereic décrit un délégué à deux arguments qui renvoie `void`. Vous l’utilisez spécifier un délégué en termes de son argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
generic<typename Arg1,  
    typename Arg2>  
    delegate void binary_delegate(Arg1, Arg2);  
```  
  
#### <a name="parameters"></a>Paramètres  
 arg1  
 Le type du premier argument.  
  
 Arg2  
 Le type du second argument.  
  
### <a name="remarks"></a>Notes  
 Le délégué genereic décrit une fonction de deux arguments qui retourne `void`.  
  
 Notez que pour :  
  
 `binary_delegate_noreturn<int, int> Fun1;`  
  
 `binary_delegate_noreturn<int, int> Fun2;`  
  
 les types `Fun1` et `Fun2` sont des synonymes, tandis que pour :  
  
 `delegate void Fun1(int, int);`  
  
 `delegate void Fun2(int, int);`  
  
 ils ne sont pas du même type.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_binary_delegate_noreturn.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
void key_compare(wchar_t left, wchar_t right)   
    {   
    System::Console::WriteLine("compare({0}, {1}) = {2}",   
        left, right, left < right);   
    }   
  
typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    kcomp(L'a', L'a');   
    kcomp(L'a', L'b');   
    kcomp(L'b', L'a');   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(a, a) = False  
compare(a, b) = True  
compare(b, a) = False  
```  

## <a name="binary_negate"></a> binary_negate (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne la logique pas de son stockée functor de deux arguments. Vous l’utilisez spécifier un objet de fonction en termes de son functor stockée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun>  
    ref class binary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    explicit binary_negate(Fun% functor);  
    binary_negate(binary_negate<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 amusement  
 Le type de la fonction stockée.  
  
## <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
|stored_function_type|Le type de foncteur.|  
  
|Membre|Description|  
|------------|-----------------|  
|binary_negate|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type^()|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments qui stocke un autre functor de deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne la logique pas de la fonction stockée appelée avec les deux arguments.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_binary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::less<int> less_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(),   
        cliext::binary_negate<cliext::less<int> >(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::not2(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
1 0  
1 0  
```  

## <a name="bind1st"></a> bind1st (STL/CLR)
Génère un `binder1st` pour un argument et un functor.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun,  
    typename Arg>  
    binder1st<Fun> bind1st(Fun% functor,  
        Arg left);  
```  
  
#### <a name="template-parameters"></a>Paramètres de modèle  
 Arg  
 Type de l’argument.  
  
 amusement  
 Le type de foncteur.  
  
#### <a name="function-parameters"></a>Paramètres de fonction  
 functor  
 La fonction à encapsuler.  
  
 left  
 Le premier argument de retour à la ligne.  
  
### <a name="remarks"></a>Notes  
 La fonction de modèle retourne [binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`. Vous l’utiliser comme un moyen pratique d’encapsuler un functor deux arguments et son premier argument à un functor un argument qui l’appelle avec un deuxième argument.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_bind1st.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
-1 0  
-1 0  
```  

## <a name="bind2nd"></a> bind2nd (STL/CLR)
Génère un `binder2nd` pour un argument et un functor.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun,  
    typename Arg>  
    binder2nd<Fun> bind2nd(Fun% functor,  
        Arg right);  
```  
  
#### <a name="template-parameters"></a>Paramètres de modèle  
 Arg  
 Type de l’argument.  
  
 amusement  
 Le type de foncteur.  
  
#### <a name="function-parameters"></a>Paramètres de fonction  
 functor  
 La fonction à encapsuler.  
  
 droite  
 Le deuxième argument de retour à la ligne.  
  
### <a name="remarks"></a>Notes  
 La fonction de modèle retourne [binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`. Vous l’utiliser comme un moyen pratique d’encapsuler un functor deux arguments et le second argument dans un functor un argument qui l’appelle avec un premier argument.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_bind2nd.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        sub4);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind2nd(sub_op, 4));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
0 -1  
0 -1  
```  

## <a name="binder1st"></a> binder1st (STL/CLR)
La classe de modèle décrit un functor un argument qui, lorsqu’elle est appelée, retourne sa functor deux arguments stockée appelée avec le premier argument stockée et le deuxième argument fourni. Vous l’utilisez spécifier un objet de fonction en termes de son functor stockée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun>  
    ref class binder1st  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        second_argument_type, result_type>  
        delegate_type;  
  
    binder1st(Fun% functor, first_argument_type left);  
    binder1st(binder1st<Arg>% right);  
  
    result_type operator()(second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 amusement  
 Le type de la fonction stockée.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
|stored_function_type|Le type de foncteur.|  
  
|Membre|Description|  
|------------|-----------------|  
|binder1st|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type^()|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor un argument qui stocke un functor deux arguments et un premier argument. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne le résultat de l’appel de la fonction stockée avec le premier argument stocké et le deuxième argument fourni.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_binder1st.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
-1 0  
-1 0  
```  

## <a name="binder2nd"></a> binder2nd (STL/CLR)
La classe de modèle décrit un functor un argument qui, lorsqu’elle est appelée, retourne sa functor deux arguments stockée appelé avec le premier argument fourni et son deuxième argument stockée. Vous l’utilisez spécifier un objet de fonction en termes de son functor stockée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun>  
    ref class binder2nd  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        first_argument_type, result_type>  
        delegate_type;  
  
    binder2nd(Fun% functor, second_argument_type left);  
    binder2nd(binder2nd<Arg>% right);  
  
    result_type operator()(first_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 amusement  
 Le type de la fonction stockée.  
  
## <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
|stored_function_type|Le type de foncteur.|  
  
|Membre|Description|  
|------------|-----------------|  
|binder2nd|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type^()|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor un argument qui stocke un functor deux arguments et un deuxième argument. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne le résultat de l’appel de la fonction stockée avec le premier argument fourni et le deuxième argument stocké.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_binder2nd.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        sub4);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind2nd(sub_op, 4));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
0 -1  
0 -1  
```  
  
## <a name="divides"></a> divise (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne le premier argument divisé par la seconde. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class divides  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    divides();  
    divides(divides<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments et de la valeur de retour.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|divides|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type^()|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne le premier argument divisé par la seconde.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_divides.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::divides<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
2 1  
2 3  
```  

## <a name="equal_to"></a> equal_to (STL/CLR)
La classe de modèle décrit un functor que, lorsqu’elle est appelée, retourne true uniquement si le premier argument est égal au second. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class equal_to  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    equal_to();  
    equal_to(equal_to<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|equal_to|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type^()|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, il retourne true uniquement si le premier argument est égal au second.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_equal_to.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::equal_to<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
1 0  
```  

## <a name="greater"></a> supérieur (STL/CLR)
La classe de modèle décrit un functor que, lorsqu’elle est appelée, retourne true uniquement si le premier argument est supérieur au second. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class greater  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    greater();  
    greater(greater<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|greater|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, il retourne true uniquement si le premier argument est supérieur au second.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_greater.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 3 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::greater<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
3 3  
1 0  
```  

## <a name="greater_equal"></a> greater_equal (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne true uniquement si le premier argument est supérieur ou égal au second. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class greater_equal  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    greater_equal();  
    greater_equal(greater_equal<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|greater_equal|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, il retourne true uniquement si le premier argument est supérieur ou égal au second.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_greater_equal.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::greater_equal<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
1 0  
```  

## <a name="less"></a> less (STL/CLR)
La classe de modèle décrit un functor que, lorsqu’elle est appelée, retourne true uniquement si le premier argument est inférieur au second. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class less  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    less();  
    less(less<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|less|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, il retourne true uniquement si le premier argument est inférieur au second.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_less.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::less<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
0 1  
``` 

## <a name="less_equal"></a> less_equal (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne true uniquement si le premier argument est inférieur ou égal au second. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class less_equal  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    less_equal();  
    less_equal(less_equal<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|less_equal|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, il retourne true uniquement si le premier argument est inférieur ou égal au second.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_less_equal.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 3 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::less_equal<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
3 3  
0 1  
``` 

## <a name="logical_and"></a> logical_and (STL/CLR)
La classe de modèle décrit un functor que, lorsqu’elle est appelée, retourne true uniquement si le premier argument et le deuxième test en tant que la valeur true. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class logical_and  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    logical_and();  
    logical_and(logical_and<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|logical_and|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, il retourne true uniquement si le premier argument et le deuxième test en tant que true.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_logical_and.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(2);   
    c1.push_back(0);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 1 0" and " 1 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::logical_and<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
2 0  
3 0  
1 0  
``` 

## <a name="logical_not"></a> logical_not (STL/CLR)
La classe de modèle décrit un functor que, lorsqu’elle est appelée, retourne true uniquement si son argument teste comme false. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class logical_not  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    logical_not();  
    logical_not(logical_not<Arg> %right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|argument_type|Le type de l’argument functor.|  
|delegate_type|Le type du délégué générique.|  
|RESULT_TYPE|Le type du résultat functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|logical_not|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor un argument. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne true uniquement si son argument tests comme false.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_logical_not.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::logical_not<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
0 1  
``` 

## <a name="logical_or"></a> logical_or (STL/CLR)
La classe de modèle décrit un functor que, lorsqu’elle est appelée, retourne true uniquement si le premier argument ou des deuxième tests en tant que la valeur true. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class logical_or  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    logical_or();  
    logical_or(logical_or<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|logical_or|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, il retourne true uniquement si le premier argument ou tests en tant que deuxième true.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_logical_or.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(2);   
    c1.push_back(0);   
    Myvector c2;   
    c2.push_back(0);   
    c2.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 2 0" and " 0 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::logical_or<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
2 0  
0 0  
1 0  
```      

## <a name="minus"></a> moins (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne le premier argument moins le second. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class minus  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    minus();  
    minus(minus<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments et de la valeur de retour.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|minus|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne le premier argument, moins la seconde.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_minus.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::minus<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
2 1  
2 2  
``` 

## <a name="modulus"></a> modulo (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne le premier argument modulo la seconde. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class modulus  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    modulus();  
    modulus(modulus<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments et de la valeur de retour.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|modulus|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne le premier argument modulo la seconde.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_modulus.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(2);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 2" and " 3 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::modulus<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 2  
3 1  
1 0  
```   

## <a name="multiplies"></a> Multiplie (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne le premier argument heures la seconde. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class multiplies  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    multiplies();  
    multiplies(multiplies<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments et de la valeur de retour.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|multiplies|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne le premier argument heures la seconde.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_multiplies.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::multiplies<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
2 1  
8 3  
```  

## <a name="negate"></a> Negate (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne l’argument de l’opération de négation. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class negate  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    negate();  
    negate(negate<Arg>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|argument_type|Le type de l’argument functor.|  
|delegate_type|Le type du délégué générique.|  
|RESULT_TYPE|Le type du résultat functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|negate|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor un argument. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne son argument de l’opération de négation.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(-3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 -3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::negate<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 -3  
-4 3  
``` 

## <a name="not_equal_to"></a> Not_Equal_To (STL/CLR)
La classe de modèle décrit un functor que, lorsqu’elle est appelée, retourne true uniquement si le premier argument n’est pas égal à la seconde. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class not_equal_to  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    not_equal_to();  
    not_equal_to(not_equal_to<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|not_equal_to|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, il retourne true uniquement si le premier argument n’est pas égal à la seconde.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_not_equal_to.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
0 1  
```   

## <a name="not1"></a> not1 (STL/CLR)
Génère un `unary_negate` pour un functor.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun>  
    unary_negate<Fun> not1(Fun% functor);  
```  
  
#### <a name="template-parameters"></a>Paramètres de modèle  
 amusement  
 Le type de foncteur.  
  
#### <a name="function-parameters"></a>Paramètres de fonction  
 functor  
 La fonction à encapsuler.  
  
### <a name="remarks"></a>Notes  
 La fonction de modèle retourne [unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`. Vous l’utiliser comme un moyen pratique d’encapsuler un functor un argument dans un functor qui remet son NOT logique.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_not1.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
1 0  
1 0  
```  

## <a name="not2"></a> not2 (STL/CLR)
Génère un `binary_negate` pour un functor.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun>  
    binary_negate<Fun> not2(Fun% functor);  
```  
  
#### <a name="template-parameters"></a>Paramètres de modèle  
 amusement  
 Le type de foncteur.  
  
#### <a name="function-parameters"></a>Paramètres de fonction  
 functor  
 La fonction à encapsuler.  
  
### <a name="remarks"></a>Notes  
 La fonction de modèle retourne [binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`. Vous l’utiliser comme un moyen pratique d’encapsuler un functor deux arguments dans un functor qui remet son NOT logique.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_not2.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::less<int> less_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(),   
        cliext::binary_negate<cliext::less<int> >(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::not2(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
1 0  
1 0  
```  

## <a name="plus"></a> plus (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne le premier argument ainsi que la seconde. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class plus  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    plus();  
    plus(plus<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments et de la valeur de retour.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|plus|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne le premier argument ainsi que la seconde.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_plus.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::plus<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
2 1  
6 4  
```  

## <a name="unary_delegate"></a> unary_delegate (STL/CLR)
La classe genereic décrit un délégué à un argument. Vous l’utilisez spécifier en termes de ses types d’arguments et de retour d’un délégué.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
generic<typename Arg,  
    typename Result>  
    delegate Result unary_delegate(Arg);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Type de l'argument.  
  
 Résultat  
 Type de retour.  
  
### <a name="remarks"></a>Notes  
 Le délégué genereic décrit une fonction d’un argument.  
  
 Notez que pour :  
  
 `unary_delegare<int, int> Fun1;`  
  
 `unary_delegare<int, int> Fun2;`  
  
 les types `Fun1` et `Fun2` sont des synonymes, tandis que pour :  
  
 `delegate int Fun1(int);`  
  
 `delegate int Fun2(int);`  
  
 ils ne sont pas du même type.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_unary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
int hash_val(wchar_t val)   
    {   
    return ((val * 17 + 31) % 67);   
    }   
  
typedef cliext::unary_delegate<wchar_t, int> Mydelegate;   
int main()   
    {   
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 5  
hash(L'b') = 22  
```  

## <a name="unary_delegate_noreturn"></a> unary_delegate_noreturn (STL/CLR)
La classe genereic décrit un délégué à un argument qui renvoie `void`. Vous l’utilisez spécifier en termes de son type d’argument d’un délégué.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
generic<typename Arg>  
    delegate void unary_delegate_noreturn(Arg);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Type de l’argument.  
  
### <a name="remarks"></a>Notes  
 Le délégué genereic décrit une fonction d’un argument qui renvoie `void`.  
  
 Notez que pour :  
  
 `unary_delegare_noreturn<int> Fun1;`  
  
 `unary_delegare_noreturn<int> Fun2;`  
  
 les types `Fun1` et `Fun2` sont des synonymes, tandis que pour :  
  
 `delegate void Fun1(int);`  
  
 `delegate void Fun2(int);`  
  
 ils ne sont pas du même type.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_unary_delegate_noreturn.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
void hash_val(wchar_t val)   
    {   
    System::Console::WriteLine("hash({0}) = {1}",   
       val, (val * 17 + 31) % 67);   
    }   
  
typedef cliext::unary_delegate_noreturn<wchar_t> Mydelegate;   
int main()   
    {   
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);   
  
    myhash(L'a');   
    myhash(L'b');   
    return (0);   
    }  
  
```  
  
```Output  
hash(a) = 5  
hash(b) = 22  
```  

## <a name="unary_negate"></a> unary_negate (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne la logique pas de son stockée functor d’un argument. Vous l’utilisez spécifier un objet de fonction en termes de son functor stockée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun>  
    ref class unary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::argument_type argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    unary_negate(Fun% functor);  
    unary_negate(unary_negate<Fun>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 amusement  
 Le type de la fonction stockée.  
  
### <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|argument_type|Le type de l’argument functor.|  
|delegate_type|Le type du délégué générique.|  
|RESULT_TYPE|Le type du résultat functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|unary_negate|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
### <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor un argument qui stocke un autre un argument functor. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne la logique pas de la fonction stockée appelée avec l’argument.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// cliext_unary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
1 0  
1 0  
```  