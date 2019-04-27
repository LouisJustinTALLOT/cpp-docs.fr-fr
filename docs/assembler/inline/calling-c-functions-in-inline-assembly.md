---
title: Appel des fonctions C dans l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
ms.openlocfilehash: 4d12321cd90f596c94c2337e100663436d512107
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167178"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Appel des fonctions C dans l'assembly inline

**Section spécifique à Microsoft**

Un bloc `__asm` peut appeler des fonctions C, y compris des routines de bibliothèques C. L'exemple suivant appelle la routine de bibliothèque `printf` :

```cpp
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp
// processor: x86
#include <stdio.h>

char format[] = "%s %s\n";
char hello[] = "Hello";
char world[] = "world";
int main( void )
{
   __asm
   {
      mov  eax, offset world
      push eax
      mov  eax, offset hello
      push eax
      mov  eax, offset format
      push eax
      call printf
      //clean up the stack so that main can exit cleanly
      //use the unused register ebx to do the cleanup
      pop  ebx
      pop  ebx
      pop  ebx
   }
}
```

Les arguments de fonction étant passés sur la pile, il vous suffit d'effectuer un push des arguments nécessaires (pointeurs de chaîne, dans l'exemple précédent) avant d'appeler la fonction. Les arguments font l’objet d’un push dans l’ordre inverse ; ils sont donc dépilés dans l’ordre souhaité. Pour émuler l'instruction C

```cpp
printf( format, hello, world );
```

l'exemple envoie les pointeurs vers `world`, `hello` et `format`, dans cet ordre-là, puis appelle `printf`.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>