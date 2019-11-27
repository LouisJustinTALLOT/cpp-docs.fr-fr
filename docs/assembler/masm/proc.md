---
title: PROC
ms.date: 08/30/2018
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: 5d1e44fcc4adbbe012b2f31fe9c6c27511bafff1
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395026"
---
# <a name="proc"></a>PROC

Marque le début et la fin d’un bloc de procédure appelé *label*. Les instructions du bloc peuvent être appelées avec l’instruction **Call** ou la directive [Invoke](../../assembler/masm/invoke.md) .

## <a name="syntax"></a>Syntaxe

> *label* **proc** ⟦*distance*⟧ ⟦*Language-type*⟧ ⟦*Visibility*⟧ __\<__ ⟦ prologuearg *⟧* __>__ ⟦ reglist**utilise** *⟧* ⟦ ⟦ __,__ *paramètre* ⟧ __:__ *tag*... ⟧\
> ⟦**Frame** ⟦ __:__ *ehandler-Address*⟧ ⟧ \
> *instructions*\
> *étiquette* **ENDP**

## <a name="remarks"></a>Notes

⟦**Frame** ⟦ __:__ *ehandler-Address*⟧ ⟧ est valide uniquement avec ml64. exe, et fait MASM pour générer une entrée de table de fonctions dans. pdata et des informations de déroulement dans. XData pour le comportement de déroulement de la gestion structurée des exceptions d’une fonction.

Lorsque l’attribut **Frame** est utilisé, il doit être suivi d’un [. Directive ENDPROLOG](../../assembler/masm/dot-endprolog.md) .

Pour plus d’informations sur l’utilisation de ml64. exe [, consultez MASM pour x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) .

## <a name="example"></a>Exemple

```asm
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE
_text SEGMENT
Example1 PROC FRAME
   push r10
.pushreg r10
   push r15
.pushreg r15
   push rbx
.pushreg rbx
   push rsi
.pushreg rsi
.endprolog
   ; rest of function ...
   ret
Example1 ENDP
_text ENDS
END
```

Le code ci-dessus émet la table de fonctions et les informations de déroulement suivantes :

```Output
FileHeader->Machine 34404
Dumping Unwind Information for file ex2.exe

.pdata entry 1 0x00001000 0x00001023

  Unwind data: 0x00002000

    Unwind version: 1
    Unwind Flags: None
    Size of prologue: 0x08
    Count of codes: 3
    Frame register: rbp
    Frame offset: 0x0
    Unwind codes:

      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00
      Code offset: 0x05, ALLOC_SMALL, size=0x10
      Code offset: 0x01, PUSH_NONVOL, register=rbp
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
