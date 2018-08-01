---
title: GoTo, instruction (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- goto_cpp
dev_langs:
- C++
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9aae9429754dab8c539d7b94e70db72d33e4f13b
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402570"
---
# <a name="goto-statement-c"></a>goto, instruction (C++)
Le **goto** instruction transfère sans condition le contrôle à l’instruction étiquetée par l’identificateur spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
goto identifier;  
```  
  
## <a name="remarks"></a>Notes  
 L'instruction étiquetée indiquée par `identifier` doit se trouver dans la fonction actuelle. Tous les noms `identifier` sont membres d'un espace de noms interne et, par conséquent, n'interfèrent pas avec d'autres identificateurs.  
  
 Une étiquette d’instruction est uniquement explicite pour un **goto** instruction ; sinon, les étiquettes d’instruction sont ignorés. Les étiquettes ne peuvent pas être redéclarées.  
  
 Il est conseillé d’utiliser le **saut**, **continuer**, et **retourner** instructions au lieu du **goto** instruction chaque fois que possibles. Toutefois, étant donné que le **saut** instruction se termine à partir d’un seul niveau d’une boucle, vous devrez peut-être utiliser un **goto** instruction pour quitter une boucle profondément imbriquée.  
  
 Pour plus d’informations sur les étiquettes et la **goto** instruction, consultez [instructions étiquetées](../cpp/labeled-statements.md).  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, un **goto** instruction transfère le contrôle au point étiqueté `stop` lorsque `i` est égal à 3.  
  
```cpp  
// goto_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 2; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 3 )  
                goto stop;  
        }  
    }  
  
    // This message does not print:   
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop:   
    printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
```Output  
Outer loop executing. i = 0  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 1  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 2  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 3  
 Inner loop executing. j = 0  
Jumped to stop. i = 3  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de saut](../cpp/jump-statements-cpp.md)   
 [Mots clés](../cpp/keywords-cpp.md)