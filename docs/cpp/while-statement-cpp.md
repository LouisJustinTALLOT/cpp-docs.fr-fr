---
title: while, instruction (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- while_cpp
dev_langs:
- C++
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e226fdf4f8978172a187e1bfa8d53655ce368f5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463299"
---
# <a name="while-statement-c"></a>while, instruction (C++)
Exécute *instruction* à plusieurs reprises jusqu'à ce que *expression* correspond à zéro.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
while ( expression )  
   statement  
```  
  
## <a name="remarks"></a>Notes  
 Le test de *expression* a lieu avant chaque exécution de la boucle ; par conséquent, un **tandis que** boucle s’exécute à zéro ou plusieurs fois. *expression* doit être d’un type intégral, un type pointeur, ou un type de classe possédant une conversion non ambiguë un type intégral ou le type de pointeur.  
  
 Un **tandis que** boucle peut également se terminer lorsqu’une [saut](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), ou [retourner](../cpp/return-statement-cpp.md) corps est exécuté dans l’instruction. Utilisez [continuer](../cpp/continue-statement-cpp.md) pour terminer l’itération actuelle sans quitter le **tandis que** boucle. **continuer** passe le contrôle à l’itération suivante de la **tandis que** boucle.  
  
 Le code suivant utilise un **tandis que** boucle pour ajuster à la fin des traits de soulignement à partir d’une chaîne :  
  
```cpp 
// while_statement.cpp  
  
#include <string.h>  
#include <stdio.h>  
char *trim( char *szSource )  
{  
    char *pszEOS = 0;  
  
    //  Set pointer to character before terminating NULL  
    pszEOS = szSource + strlen( szSource ) - 1;  
  
    //  iterate backwards until non '_' is found   
    while( (pszEOS >= szSource) && (*pszEOS == '_') )  
        *pszEOS-- = '\0';  
  
    return szSource;  
}  
int main()  
{  
    char szbuf[] = "12345_____";  
  
    printf_s("\nBefore trim: %s", szbuf);  
    printf_s("\nAfter trim: %s\n", trim(szbuf));  
}  
```  
  
 La condition d’arrêt est évaluée en haut de la boucle. S’il n’y a aucun caractère de soulignement de fin, la boucle s’exécute jamais.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions d’itération](../cpp/iteration-statements-cpp.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [do-while, instruction (C++)](../cpp/do-while-statement-cpp.md)   
 [for, instruction (C++)](../cpp/for-statement-cpp.md)   
 [Basé sur une plage, instruction (C++)](../cpp/range-based-for-statement-cpp.md)