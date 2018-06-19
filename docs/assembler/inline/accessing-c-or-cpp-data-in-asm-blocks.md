---
title: L’accès aux données C ou C++ dans les blocs __asm | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9631db3c09c19e38791a6c909be02acd1c91601b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049757"
---
# <a name="accessing-c-or-c-data-in-asm-blocks"></a>Accès aux données C ou C++ dans les blocs __asm
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 L'un des principaux avantages offerts par l'assembleur inline est la capacité à faire référence à des variables C ou C++ par nom. Un bloc `__asm` peut faire référence à n'importe quel symbole, y compris des noms de variables, qui figure dans la portée où le bloc apparaît. Par exemple, si la variable C `var` est dans la portée, l'instruction  
  
```  
__asm mov eax, var  
```  
  
 stocke la valeur de `var` dans EAX.  
  
 Si une classe, une structure ou un membre d’union a un nom unique, un `__asm` bloc peut faire référence à l’aide uniquement le nom du membre, sans spécifier la variable ou `typedef` nom avant la période (**.**) (opérateur). En revanche, si le nom du membre n'est pas unique, vous devez placer une variable ou un nom `typedef` juste avant l'opérateur point. Par exemple, les types structure de l'exemple suivant partagent `same_name` comme nom de membre :  
  
 Si vous déclarez des variables avec les types  
  
```  
struct first_type hal;  
struct second_type oat;  
```  
  
 toutes les références au membre `same_name` doivent utiliser le nom de la variable, car `same_name` n'est pas unique. Cependant, le membre `weasel` ayant un nom unique, vous pouvez y faire référence en utilisant uniquement son nom de membre :  
  
```  
// InlineAssembler_Accessing_C_asm_Blocks.cpp  
// processor: x86  
#include <stdio.h>  
struct first_type  
{  
   char *weasel;  
   int same_name;  
};  
  
struct second_type  
{  
   int wonton;  
   long same_name;  
};  
  
int main()  
{  
   struct first_type hal;  
   struct second_type oat;  
  
   __asm  
   {  
      lea ebx, hal  
      mov ecx, [ebx]hal.same_name ; Must use 'hal'  
      mov esi, [ebx].weasel       ; Can omit 'hal'  
   }  
   return 0;  
}  
```  
  
 Notez que l'omission du nom de la variable est simplement une pratique de codage. Les mêmes instructions assembleur sont générées, que le nom de la variable soit présent ou non.  
  
 Vous pouvez accéder aux données membres en C++ sans tenir compte des restrictions d'accès. En revanche, vous ne pouvez pas appeler de fonctions membres.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)