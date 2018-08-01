---
title: Instruction de null | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab391bb75dd6e7a2ef1ccf0951fa93770e6cd316
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408774"
---
# <a name="null-statement"></a>null, instruction
Le « instruction null » est une instruction d’expression avec le *expression* manquant. Elle s'avère utile lorsque la syntaxe du langage demande une instruction, mais pas d'évaluation d'expression. Elle se compose d'un point-virgule.  
  
 Les instructions null sont couramment utilisées comme espaces réservés dans les instructions d'itération ou comme instructions sur lesquelles placer des étiquettes à la fin d'instructions composées ou de fonctions.  
  
 Le fragment de code suivant montre comment copier une chaîne vers une autre et comporte l'instruction null :  
  
```cpp 
// null_statement.cpp  
char *myStrCpy( char *Dest, const char *Source )  
{  
    char *DestStart = Dest;  
  
    // Assign value pointed to by Source to  
    // Dest until the end-of-string 0 is  
    // encountered.  
    while( *Dest++ = *Source++ )  
        ;   // Null statement.  
  
    return DestStart;  
}  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction d’expression](../cpp/expression-statement.md)