---
description: 'En savoir plus sur : accéder aux étiquettes dans l’assembly inline'
title: Accès aux étiquettes dans l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
ms.openlocfilehash: b4a32dd9baace77245f612d68b58f954a81075ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117716"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Accès aux étiquettes dans l'assembly inline

**Spécifique à Microsoft**

À l’instar d’une étiquette C ou C++ ordinaire, une étiquette dans un **`__asm`** bloc a une portée dans la fonction dans laquelle elle est définie (non seulement dans le bloc). Les instructions d’assembly et les **`goto`** instructions peuvent accéder aux étiquettes à l’intérieur ou à l’extérieur du **`__asm`** bloc.

Les étiquettes définies dans les **`__asm`** blocs ne respectent pas la casse ; les **`goto`** instructions et les instructions d’assembly peuvent faire référence à ces étiquettes sans tenir compte de la casse. Les étiquettes C et C++ respectent la casse uniquement lorsqu’elles sont utilisées par des **`goto`** instructions. Les instructions assembleur peuvent accéder à une étiquette C ou C++ sans tenir compte de la casse.

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

N’utilisez pas de noms de fonction de bibliothèque C comme étiquettes dans des **`__asm`** blocs. Par exemple, vous pouvez être tenté d'utiliser `exit` comme étiquette de la façon suivante :

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

Comme **Exit** est le nom d’une fonction de bibliothèque C, ce code peut provoquer un saut vers la fonction **Exit** au lieu de l’emplacement souhaité.

Comme dans les programmes MASM, le symbole dollar (`$`) sert de compteur de position actuelle. C'est une étiquette pour l'instruction en cours d'assemblage. Dans **`__asm`** les blocs, son utilisation principale consiste à effectuer de longs sauts conditionnels :

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
