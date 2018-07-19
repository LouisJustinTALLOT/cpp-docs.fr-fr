---
title: Instruction return dans la terminaison du programme (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb594eb10e8068d5f5b3ed124d5e77b48ced728e
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942629"
---
# <a name="return-statement-in-program-termination-c"></a>Instruction return dans la terminaison du programme (C++)
Émission d’un `return` instruction à partir de **principal** est fonctionnellement équivalent à l’appel le **quitter** (fonction). Prenons l'exemple suivant :  
  
```cpp 
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 Le **quitter** et **retourner** dans l’exemple précédent, les instructions sont fonctionnellement identiques. Toutefois, C++ exige que fonctions dont les types de retour autre que **void** retournent une valeur. Le **retourner** instruction vous permet de retourner une valeur à partir de `main`.  
  
## <a name="see-also"></a>Voir aussi  
 [Terminaison du programme](../cpp/program-termination.md)