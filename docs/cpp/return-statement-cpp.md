---
title: return, instruction (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- return_cpp
dev_langs:
- C++
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aea9999adc7089499028850017a32245bba97db6
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942850"
---
# <a name="return-statement-c"></a>return, instruction (C++)
Termine l'exécution d'une fonction et retourne le contrôle à la fonction d'appel (ou au système d'exploitation si vous transférez le contrôle à partir de la fonction `main`). L'exécution reprend dans la fonction d'appel au point immédiatement après l'appel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
return [expression];  
```  
  
## <a name="remarks"></a>Notes  
 La clause `expression`, si elle est présente, est convertie dans le type spécifié dans la déclaration de fonction, comme si une initialisation était exécutée. Conversion du type de l’expression à la **retourner** type de la fonction peut créer des objets temporaires. Pour plus d’informations sur quand et comment les objets temporaires sont créés, consultez [objets temporaires](../cpp/temporary-objects.md).  
  
 La valeur de la clause `expression` est retournée à la fonction d'appel. Si l'expression est omise, la valeur de retour de la fonction n'est pas définie. Constructeurs et destructeurs et fonctions de type **void**, ne peut pas spécifier une expression dans le **retourner** instruction. Fonctions de tous les autres types doivent spécifier une expression dans le **retourner** instruction.  
  
 Lorsque le flux de contrôle quitte le bloc englobant la définition de fonction, le résultat est le même comme il le serait si un **retourner** instruction sans expression avait été exécutée. Ceci n'est pas valable pour les fonctions déclarées comme retournant une valeur.  
  
 Une fonction peut avoir un nombre quelconque de **retourner** instructions.  
  
 L’exemple suivant utilise une expression avec un **retourner** instruction pour obtenir le plus grand de deux entiers.  
  
## <a name="example"></a>Exemple  
  
```cpp 
// return_statement2.cpp  
#include <stdio.h>  
  
int max ( int a, int b )  
{  
   return ( a > b ? a : b );  
}  
  
int main()  
{  
    int nOne = 5;  
    int nTwo = 7;  
  
    printf_s("\n%d is bigger\n", max( nOne, nTwo ));  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de saut](../cpp/jump-statements-cpp.md)   
 [Mots clés](../cpp/keywords-cpp.md)