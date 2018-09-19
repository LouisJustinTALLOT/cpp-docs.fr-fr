---
title: faire-while, instruction (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- do_cpp
dev_langs:
- C++
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37155be11caaee9c609a0e11ddbfeb5d62856903
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071196"
---
# <a name="do-while-statement-c"></a>do-while, instruction (C++)

Exécute un *instruction* à plusieurs reprises jusqu'à ce que la condition d’arrêt spécifié (la *expression*) correspond à zéro.

## <a name="syntax"></a>Syntaxe

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Notes

Le test de la condition d’arrêt est effectué après chaque exécution de la boucle ; Par conséquent, un **faire-tandis que** boucle exécute une ou plusieurs fois, selon la valeur de l’expression d’arrêt. Le **faire-tandis que** instruction peut également se terminer lorsqu’une [saut](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), ou [retourner](../cpp/return-statement-cpp.md) instruction est exécutée dans le corps d’instruction.

L'élément *expression* doit être de type arithmétique ou pointeur. L'exécution se déroule comme suit :

1. Le corps de l'instruction est exécuté.

1. Ensuite, l'élément *expression* est évalué. Si *expression* a la valeur false, le **faire-tandis que** instruction se termine et le contrôle passe à l’instruction suivante dans le programme. Si l'élément *expression* est true (différent de zéro), le processus se répète, en commençant à l'étape 1.

## <a name="example"></a>Exemple

L’exemple suivant montre comment la **faire-tandis que** instruction :

```cpp
// do_while_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        printf_s("\n%d",i++);
    } while (i < 3);
}
```

## <a name="see-also"></a>Voir aussi

[Instructions d’itération](../cpp/iteration-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[while, instruction (C++)](../cpp/while-statement-cpp.md)<br/>
[for, instruction (C++)](../cpp/for-statement-cpp.md)<br/>
[Basé sur une plage, instruction (C++)](../cpp/range-based-for-statement-cpp.md)