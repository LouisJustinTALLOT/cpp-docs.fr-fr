---
title: equal_to, struct | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- equal_to
- xfunctional/std::equal_to
dev_langs:
- C++
helpviewer_keywords:
- equal_to function
- equal_to struct
ms.assetid: 8e4f2b50-b2db-48e3-b4cc-6cc03362c2a6
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: bac0d0114b10fc4ac7a83a60f21db5218cb3f1c8
ms.contentlocale: fr-fr
ms.lasthandoff: 04/19/2017

---
# <a name="equalto-struct"></a>equal_to, struct
Prédicat binaire qui effectue l’opération d’égalité ( `operator==`) sur ses arguments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Type = void>  
struct equal_to : public binary_function<Type, Type, bool>   
 {  
    bool operator()(const Type& Left, const Type& Right) const; 
 };  
 
// specialized transparent functor for operator== 
template <>  
struct equal_to<void>  
 {  
    template <class T, class U>  
    auto operator()(T&& Left, U&& Right) const 
      ->  decltype(std::forward<T>(Left) == std::forward<U>(Right));
 };  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Type`, `T`, `U`  
 Tout type qui prend en charge un `operator==` qui accepte des opérandes des types spécifiés ou inférés.  
  
 `Left`  
 Opérande gauche de l’opération d’égalité. Le modèle non spécialisé prend un argument de référence lvalue de type `Type`. Le modèle spécialisé effectue un transfert parfait des arguments de référence lvalue et rvalue du type inféré `T`.  
  
 `Right`  
 Opérande droit de l’opération d’égalité. Le modèle non spécialisé prend un argument de référence lvalue de type `Type`. Le modèle spécialisé effectue un transfert parfait des arguments de référence lvalue et rvalue du type inféré `U`.  
  
## <a name="return-value"></a>Valeur de retour  
 Résultat de `Left``==``Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator==`.  
  
## <a name="remarks"></a>Remarques  
 L’égalité des objets de type `Type` doit pouvoir être comparée. `operator==` défini sur l’ensemble d’objets doit donc satisfaire les propriétés mathématiques d’une relation d’équivalence. Tous les types pointeur et numériques intégrés répondent à cette exigence.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// functional_equal_to.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v1, v2, v3 ( 6 );  
   vector <double>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i+=2 )  
   {  
      v1.push_back( 2.0 *i );  
      v1.push_back( 2.0 * i + 1.0 );  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j+=2 )  
   {  
      v2.push_back( - 2.0 * j );  
      v2.push_back( 2.0 * j + 1.0 );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Testing for the element-wise equality between v1 & v2  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),   
      equal_to<double>( ) );  
  
   cout << "The result of the element-wise equal_to comparison\n"  
      << "between v1 & v2 is: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 1 4 5 8 9 )  
The vector v2 = ( -0 1 -4 5 -8 9 )  
The result of the element-wise equal_to comparison  
between v1 & v2 is: ( 1 1 0 1 0 1 )  
```


