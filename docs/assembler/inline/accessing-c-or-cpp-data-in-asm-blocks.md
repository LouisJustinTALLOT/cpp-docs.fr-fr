---
description: 'En savoir plus sur : accès aux données C ou C++ dans les blocs __asm'
title: Accès aux données C ou C++ dans les blocs __asm
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: b24d25b5687dd309c400b17c1e0eb6b35ef986f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118080"
---
# <a name="accessing-c-or-c-data-in-__asm-blocks"></a>Accès aux données C ou C++ dans les blocs __asm

**Spécifique à Microsoft**

L'un des principaux avantages offerts par l'assembleur inline est la capacité à faire référence à des variables C ou C++ par nom. Un **`__asm`** bloc peut faire référence à n’importe quel symbole, y compris les noms de variables, qui se trouvent dans la portée où le bloc apparaît. Par exemple, si la variable C `var` est dans la portée, l'instruction

```cpp
__asm mov eax, var
```

stocke la valeur de `var` dans EAX.

Si un membre de classe, de structure ou d’Union a un nom unique, un **`__asm`** bloc peut y faire référence en utilisant uniquement le nom du membre, sans spécifier la variable ou le **`typedef`** nom avant l’opérateur point (**.**). Toutefois, si le nom de membre n’est pas unique, vous devez placer une variable ou un **`typedef`** nom juste avant l’opérateur point. Par exemple, les types structure de l'exemple suivant partagent `same_name` comme nom de membre :

Si vous déclarez des variables avec les types

```cpp
struct first_type hal;
struct second_type oat;
```

toutes les références au membre `same_name` doivent utiliser le nom de la variable, car `same_name` n'est pas unique. Cependant, le membre `weasel` ayant un nom unique, vous pouvez y faire référence en utilisant uniquement son nom de membre :

```cpp
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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
