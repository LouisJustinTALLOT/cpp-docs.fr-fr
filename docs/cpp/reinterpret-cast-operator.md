---
title: reinterpret_cast, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- reinterpret_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18a7cdd80c1d7b6b17a988d8f3581c7757f69823
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942865"
---
# <a name="reinterpretcast-operator"></a>reinterpret_cast, opérateur
Autorise la conversion de tout pointeur en tout autre type pointeur. Autorise également la conversion de tout type entier en tout type pointeur et vice versa.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reinterpret_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>Notes  
 Utilisation incorrecte de la **reinterpret_cast** opérateur peut facilement être unsafe. À moins que la conversion souhaitée soit fondamentalement de bas niveau, vous devez utiliser l'un des autres opérateurs de cast.  
  
 Le **reinterpret_cast** opérateur peut être utilisé pour les conversions comme `char*` à `int*`, ou `One_class*` à `Unrelated_class*`, qui sont fondamentalement risquées.  
  
 Le résultat d’une **reinterpret_cast** ne peut pas être utilisé sans risque pour autre chose que la reconversion vers son type d’origine. Les autres utilisations sont, au mieux, non portables.  
  
 Le **reinterpret_cast** opérateur ne peut pas caster le **const**, **volatile**, ou **__unaligned** attributs. Consultez [const_cast, opérateur](../cpp/const-cast-operator.md) pour plus d’informations sur la suppression de ces attributs.  
  
 Le **reinterpret_cast** opérateur convertit une valeur de pointeur null à la valeur de pointeur null du type de destination.  
  
 Une utilisation pratique de **reinterpret_cast** est dans une fonction de hachage, qui mappent une valeur à un index de telle sorte que deux distinctes des valeurs rarement fin inscrire avec le même index.  
  
```cpp 
#include <iostream>  
using namespace std;  
  
// Returns a hash code based on an address  
unsigned short Hash( void *p ) {  
   unsigned int val = reinterpret_cast<unsigned int>( p );  
   return ( unsigned short )( val ^ (val >> 16));  
}  
  
using namespace std;  
int main() {  
   int a[20];  
   for ( int i = 0; i < 20; i++ )  
      cout << Hash( a + i ) << endl;  
}  
  
Output:   
64641  
64645  
64889  
64893  
64881  
64885  
64873  
64877  
64865  
64869  
64857  
64861  
64849  
64853  
64841  
64845  
64833  
64837  
64825  
64829  
```  
  
 Le **reinterpret_cast** permet le pointeur est traitée comme un type intégral. Le résultat binaire est alors déplacé et soumis à une opération XOR avec lui-même pour produire un index unique (à un niveau de probabilité élevé). L’index est ensuite tronqué par un cast de style C standard en type de retour de la fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs de casting](../cpp/casting-operators.md)   
 [Mots clés](../cpp/keywords-cpp.md)