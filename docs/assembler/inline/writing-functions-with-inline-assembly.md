---
description: 'En savoir plus sur : écriture de fonctions avec un assembly inline'
title: Écriture de fonctions avec un assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
ms.openlocfilehash: 94a1e03842620982e74818dbf2f1bd492a2a4738
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97121801"
---
# <a name="writing-functions-with-inline-assembly"></a>Écriture de fonctions avec un assembly inline

**Spécifique à Microsoft**

Si vous écrivez une fonction avec du code assembleur inline, il est facile de transmettre des arguments à cette fonction et de retourner une valeur de celle-ci. Les exemples suivants comparent une fonction d'abord écrite pour un assembleur distinct puis réécrite pour l'assembleur inline. La fonction, appelée `power2`, reçoit deux paramètres, multipliant le premier paramètre par 2 à la puissance du second paramètre. Écrite pour un assembleur distinct, la fonction peut ressembler à ceci :

```asm
; POWER.ASM
; Compute the power of an integer
;
       PUBLIC _power2
_TEXT SEGMENT WORD PUBLIC 'CODE'
_power2 PROC

        push ebp        ; Save EBP
        mov ebp, esp    ; Move ESP into EBP so we can refer
                        ;   to arguments on the stack
        mov eax, [ebp+4] ; Get first argument
        mov ecx, [ebp+6] ; Get second argument
        shl eax, cl     ; EAX = EAX * ( 2 ^ CL )
        pop ebp         ; Restore EBP
        ret             ; Return with sum in EAX

_power2 ENDP
_TEXT   ENDS
        END
```

Étant donné qu'elle est écrite pour un assembleur distinct, la fonction nécessite un fichier source distinct ainsi qu'un code assembleur et des étapes de liaison. Les arguments de fonction C et C++ sont généralement transmis sur la pile, par conséquent cette version de la fonction `power2` accède à ses arguments par leur position sur la pile. (Notez que la directive **Model** , disponible dans MASM et certains autres assembleurs, vous permet également d’accéder aux arguments de pile et aux variables de pile locales par nom.)

## <a name="example"></a>Exemple

Ce programme écrit la fonction `power2` avec le code assembleur inline :

```cpp
// Power2_inline_asm.c
// compile with: /EHsc
// processor: x86

#include <stdio.h>

int power2( int num, int power );

int main( void )
{
    printf_s( "3 times 2 to the power of 5 is %d\n", \
              power2( 3, 5) );
}
int power2( int num, int power )
{
   __asm
   {
      mov eax, num    ; Get first argument
      mov ecx, power  ; Get second argument
      shl eax, cl     ; EAX = EAX * ( 2 to the power of CL )
   }
   // Return with result in EAX
}
```

La version inline de la fonction `power2` fait référence à ses arguments par nom et apparaît dans le même fichier source que le reste du programme. Cette version requiert également moins d'instructions assembleur.

Étant donné que la version inline de `power2` n’exécute pas d' **`return`** instruction C, elle provoque un avertissement sans gravité si vous effectuez une compilation au niveau d’avertissement 2 ou supérieur. La fonction ne retourne pas de valeur, mais le compilateur ne peut pas indiquer qu’en l’absence d’une **`return`** instruction. Vous pouvez utiliser [#pragma AVERTISSEMENT](../../preprocessor/warning.md) pour désactiver la génération de cet avertissement.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
