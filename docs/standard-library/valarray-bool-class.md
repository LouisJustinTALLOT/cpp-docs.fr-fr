---
title: valarray&lt;bool&gt;, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- valarray<bool>
- valarray/std::valarray<bool>
dev_langs: C++
helpviewer_keywords: valarray<bool> class
ms.assetid: fc0e7121-4758-4ea5-86c3-f04448f04acf
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: feb010742f56e5bea9197e896f11619678578385
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="valarrayltboolgt-class"></a>valarray&lt;bool&gt;, classe
Version spécialisée de la classe de modèle **valarray\<Type>** pour les éléments de type `bool`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class valarray<bool>  
```  
  
## <a name="example"></a>Exemple  
  
```cpp  
// valarray_bool.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaBool ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )   
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )   
      vaL [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i++ )   
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaBool = ( vaL < vaR );  
   cout << "The result of the less-than comparison "  
   << "test is the\n valarray<bool>: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaBool [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The result of the less-than comparison test is the  
 valarray<bool>: ( 0 0 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<valarray>  
  
 **Espace de noms :** std  
  
## <a name="see-also"></a>Voir aussi  
 [valarray, classe](../standard-library/valarray-class.md)   
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
