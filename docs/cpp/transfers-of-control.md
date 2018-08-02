---
title: Transferts de contrôle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e773a0188eb3450ab1a13a24fc556fa8e8c4f874
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464267"
---
# <a name="transfers-of-control"></a>Transferts de contrôle
Vous pouvez utiliser la **goto** instruction ou un **cas** étiquette dans un **basculer** instruction pour spécifier un programme branche après un initialiseur. Ce code est conforme sauf si la déclaration qui contient l'initialiseur figure dans un bloc se trouvant lui-même dans le bloc dans lequel l'instruction de saut s'exécute.  
  
 L'exemple suivant montre une boucle qui déclare et initialise les objets `total`, `ch` et `i`. Il est également un erronée **goto** instruction qui transfère le contrôle après un initialiseur.  
  
```cpp 
// transfers_of_control.cpp  
// compile with: /W1  
// Read input until a nonnumeric character is entered.  
int main()  
{  
   char MyArray[5] = {'2','2','a','c'};  
   int i = 0;  
   while( 1 )  
   {  
      int total = 0;  
  
      char ch = MyArray[i++];  
  
      if ( ch >= '0' && ch <= '9' )  
      {  
         goto Label1;  
  
         int i = ch - '0';  
      Label1:  
         total += i;   // C4700: transfers past initialization of i.  
      } // i would be destroyed here if  goto error were not present  
   else  
      // Break statement transfers control out of loop,  
      //  destroying total and ch.  
      break;  
   }  
}  
```  
  
 Dans l’exemple précédent, le **goto** instruction tente de transférer le contrôle après l’initialisation de `i`. Toutefois, si `i` était déclaré mais non initialisé, le transfert serait conforme.  
  
 Les objets `total` et `ch`, déclarés dans le bloc qui sert le *instruction* de la **tandis que** instruction, sont détruits lors de la sortie de ce bloc à l’aide de la  **saut** instruction.  