---
title: logical_not, struct | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::logical_not
dev_langs: C++
helpviewer_keywords:
- logical_not class
- logical_not struct
ms.assetid: 892db678-31da-4540-974b-17b05efc0849
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 28d04e39518584249ee6cbd1d0966dc0d4eb9f52
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="logicalnot-struct"></a>logical_not, struct
Objet de fonction prédéfini qui effectue l’opération NOT logique ( `operator!`) sur ses arguments.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Type = void>
struct logical_not : public unary_function<Type, bool>  
{
    bool operator()(const Type& Left) const;
};

// specialized transparent functor for operator!
template <>
struct logical_not<void>  
{
  template <class Type>
  auto operator()(Type&& Left) const`
     -> decltype(!std::forward<Type>(Left));
 };
```  
  
#### <a name="parameters"></a>Paramètres  
 `Type`  
 Tout type qui prend en charge un `operator!` qui accepte un opérande du type spécifié ou déduit.  
  
 `Left`  
 Opérande de l’opération NOT logique. Le modèle non spécialisé prend un argument de référence lvalue de type `Type`. Le modèle spécialisé effectue un transfert parfait des arguments de référence lvalue et rvalue du type inféré `Type`.  
  
## <a name="return-value"></a>Valeur de retour  
 Résultat de `!Left`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator!`.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// functional_logical_not.cpp  
// compile with: /EHsc  
#include <deque>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   deque<bool> d1, d2 ( 7 );  
   deque<bool>::iterator iter1, iter2;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )  
   {  
      d1.push_back((bool)((i % 2) != 0));  
   }  
  
   cout << boolalpha;    // boolalpha I/O flag on  
  
   cout << "Original deque:\n d1 = ( " ;  
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )  
      cout << *iter1 << " ";  
   cout << ")" << endl;  
  
   // To flip all the truth values of the elements,  
   // use the logical_not function object  
   transform( d1.begin( ), d1.end( ), d2.begin( ),logical_not<bool>( ) );  
   cout << "The deque with its values negated is:\n d2 = ( " ;  
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )  
      cout << *iter2 << " ";  
   cout << ")" << endl;  
}  
/* Output:  
Original deque:  
 d1 = ( false true false true false true false )  
The deque with its values negated is:  
 d2 = ( true false true false true false true )  
 */  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<functional>  
  
 **Espace de noms :** std  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)



