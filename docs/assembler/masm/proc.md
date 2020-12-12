---
description: 'En savoir plus sur : PROC'
title: PROC
ms.date: 12/06/2019
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: fe811ed1723dc1a41014720d97b6f21ab596c2e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97126033"
---
# <a name="proc"></a>PROC

Marque le début et la fin d’un bloc de procédure appelé *label*. Les instructions du bloc peuvent être appelées avec l’instruction **Call** ou la directive [Invoke](invoke.md) .

## <a name="syntax"></a>Syntaxe

> *label* **proc** ⟦*distance*⟧ ⟦*Language-type*⟧ ⟦ **public**  |  **Private**  |  **Export** ⟧ ⟦ __\<__*prologuearg*__>__ ⟧ ⟦**utilise** *reglist*⟧ ⟦__,__ *paramètre* ⟦__:__*tag*⟧... ⟧\
> ⟦**Frame** ⟦__:__*ehandler-Address*⟧ ⟧ \
> *publication*\
> *étiquette* **ENDP**

## <a name="remarks"></a>Notes

Les arguments ⟦*distance*⟧ et ⟦*Language-type*⟧ sont valides uniquement dans MASM 32 bits.

⟦**Frame** ⟦__:__*ehandler-Address*⟧ ⟧ est uniquement valide avec ml64.exe, et fait MASM pour générer une entrée de table de fonctions dans. pdata et des informations de déroulement dans. XData pour le comportement de déroulement de la gestion structurée des exceptions d’une fonction.

Lorsque l’attribut **Frame** est utilisé, il doit être suivi d’un [. Directive ENDPROLOG](dot-endprolog.md) .

Pour plus d’informations sur l’utilisation de ml64.exe [, consultez MASM pour x64 (ml64.exe)](masm-for-x64-ml64-exe.md) .

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

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
