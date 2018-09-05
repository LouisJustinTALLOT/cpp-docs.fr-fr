---
title: Accéder aux étiquettes dans l’Assembly Inline | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e697df32218c3e2bcdeb03cde44b7b5d854cb7b0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693622"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Accès aux étiquettes dans l'assembly inline

**Section spécifique à Microsoft**

Tout comme une étiquette ordinaire C ou C++, une étiquette de bloc `__asm` a une portée qui s'étend à l'ensemble de la fonction dans laquelle il est défini (non seulement dans le bloc). Les instructions assembleur et les instructions `goto` peuvent accéder aux étiquettes à l'intérieur ou à l'extérieur du bloc `__asm`.

Les étiquettes définies dans les blocs `__asm` ne respectent pas la casse. Les instructions `goto` et les instructions assembleur peuvent faire référence à ces étiquettes sans tenir compte de la casse. Les étiquettes C et C++ respectent la casse uniquement lorsqu'elles sont utilisées par les instructions `goto`. Les instructions assembleur peuvent accéder à une étiquette C ou C++ sans tenir compte de la casse.

Le code suivant illustre toutes les permutations :

```cpp
void func( void )
{
   goto C_Dest;  /* Legal: correct case   */
   goto c_dest;  /* Error: incorrect case */

   goto A_Dest;  /* Legal: correct case   */
   goto a_dest;  /* Legal: incorrect case */

   __asm
   {
      jmp C_Dest ; Legal: correct case
      jmp c_dest ; Legal: incorrect case

      jmp A_Dest ; Legal: correct case
      jmp a_dest ; Legal: incorrect case

      a_dest:    ; __asm label
   }

   C_Dest:       /* C label */
   return;
}
int main()
{
}
```

N'utilisez pas de noms de fonction de bibliothèque C dans les blocs `__asm`. Par exemple, vous pouvez être tenté d'utiliser `exit` comme étiquette de la façon suivante :

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

Étant donné que **quitter** est le nom d’une fonction de bibliothèque C, ce code peut provoquer un saut vers le **quitter** fonction au lieu d’à l’emplacement souhaité.

Comme dans les programmes MASM, le symbole dollar (`$`) sert de compteur de position actuelle. C'est une étiquette pour l'instruction en cours d'assemblage. Dans les blocs `__asm`, son utilisation principale consiste à créer de longs sauts conditionnels :

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>