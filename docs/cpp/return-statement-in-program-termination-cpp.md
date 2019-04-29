---
title: Instruction return dans la terminaison du programme (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
ms.openlocfilehash: 9c7b6130ee1a0b49ab75a70d84764d3a1f8c5ef0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267610"
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