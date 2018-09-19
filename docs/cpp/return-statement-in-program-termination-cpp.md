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
ms.openlocfilehash: cfcf65258767178c0f74f63ca6e938e1d940e3be
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061134"
---
# <a name="return-statement-in-program-termination-c"></a>Instruction return dans la terminaison du programme (C++)

Émission d’un **retourner** instruction à partir de `main` est fonctionnellement équivalent à l’appel le `exit` (fonction). Prenons l'exemple suivant :

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Le `exit` et **retourner** dans l’exemple précédent, les instructions sont fonctionnellement identiques. Toutefois, C++ exige que fonctions dont les types de retour autre que **void** retournent une valeur. Le **retourner** instruction vous permet de retourner une valeur à partir de `main`.

## <a name="see-also"></a>Voir aussi

[Terminaison du programme](../cpp/program-termination.md)