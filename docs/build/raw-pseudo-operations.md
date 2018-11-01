---
title: Pseudo-opérations brutes
ms.date: 11/04/2016
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
ms.openlocfilehash: 04dfe4d59c05dfcf22d0e64063fbc4953cbcb2f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538027"
---
# <a name="raw-pseudo-operations"></a>Pseudo-opérations brutes

Cette rubrique répertorie les pseudo-opérations.

## <a name="remarks"></a>Notes

|Opération de pseudo|Description|
|----------------------|-----------------|
|FRAME de PROC [ : ehandler]|Causes MASM pour générer une fonction table d’entrée dans .pdata et .xdata d’informations de déroulement pour une fonction de structuré comportement de déroulement de la gestion des exceptions.  Si ehandler est présent, cette procédure est entrée dans l’enregistrement .xdata comme gestionnaire spécifique au langage.<br /><br /> Lorsque l’attribut FRAME est utilisé, il doit être suivi par un. Directive ENDPROLOG.  Si la fonction est une fonction de feuille (tel que défini dans [Types de fonction](../build/function-types.md)) l’attribut FRAME n’est pas nécessaire, tout comme le reste de ces pseudo-opérations.|
|. PUSHREG reg|Génère une entrée de code de déroulement UWOP_PUSH_NONVOL pour le numéro de Registre spécifié à l’aide de l’offset actuel dans le prologue.<br /><br /> Cela doit uniquement être utilisé avec les registres d’entiers non volatile.  Pour obtenir des notifications Push registres volatils, utilisez un. 8 ALLOCSTACK, à la place|
|. SETFRAME reg, offset|Renseigne le frame inscrire champ et le décalage dans les informations de déroulement en utilisant le Registre spécifié et le décalage. Le décalage doit être un multiple de 16 et inférieur ou égal à 240. Cette directive génère également une entrée de code de déroulement UWOP_SET_FPREG pour le Registre spécifié à l’aide de l’offset de prologue actuel.|
|. Taille ALLOCSTACK|Génère un UWOP_ALLOC_SMALL ou UWOP_ALLOC_LARGE avec la taille spécifiée pour l’offset actuel dans le prologue.<br /><br /> L’opérande de taille doit être un multiple de 8.|
|. SAVEREG reg, offset|Génère un UWOP_SAVE_NONVOL ou une entrée de code de déroulement UWOP_SAVE_NONVOL_FAR pour le Registre spécifié et l’offset à l’aide de l’offset de prologue actuel. MASM choisira l’encodage le plus efficace.<br /><br /> Offset doit être positif et un multiple de 8.  Décalage est relatif à la base du frame de la procédure, qui est généralement dans RSP, ou, si vous utilisez un pointeur de frame, le pointeur de frame non ajustée.|
|. SAVEXMM128 reg, offset|Génère un UWOP_SAVE_XMM128 ou une entrée de code de déroulement UWOP_SAVE_XMM128_FAR pour le registre XMM spécifié et l’offset à l’aide de l’offset de prologue actuel. MASM choisira l’encodage le plus efficace.<br /><br /> Offset doit être positif et un multiple de 16.  Décalage est relatif à la base du frame de la procédure, qui est généralement dans RSP, ou, si vous utilisez un pointeur de frame, le pointeur de frame non ajustée.|
|. PUSHFRAME [code]|Génère une entrée de code de déroulement UWOP_PUSH_MACHFRAME. Si le code facultatif est spécifié, l’écriture de code de déroulement reçoit un modificateur de 1. Sinon, le modificateur est 0.|
|.ENDPROLOG|Signale la fin des déclarations de prologue.  Doit se produire dans les 255 premiers octets de la fonction.|

Voici un exemple de prologue de fonction avec une utilisation correcte de la plupart des codes d’opération :

```
sample PROC FRAME
   db      048h; emit a REX prefix, to enable hot-patching
push rbp
.pushreg rbp
sub rsp, 040h
.allocstack 040h
lea rbp, [rsp+020h]
.setframe rbp, 020h
movdqa [rbp], xmm7
.savexmm128 xmm7, 020h;the offset is from the base of the frame
;not the scaled offset of the frame
mov [rbp+018h], rsi
.savereg rsi, 038h
mov [rsp+010h], rdi
.savereg rdi, 010h; you can still use RSP as the base of the frame
; or any other register you choose
.endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn’t have a frame pointer, this would be illegal
; if we didn’t make this modification,
; there would be no need for a frame pointer

sub rsp, 060h

; we can unwind from the following AV because of the frame pointer

mov rax, 0
mov rax, [rax] ; AV!

; restore the registers that weren’t saved with a push
; this isn’t part of the official epilog, as described in section 2.5

movdqa xmm7, [rbp]
mov rsi, [rbp+018h]
mov rdi, [rbp-010h]

; Here’s the official epilog

lea rsp, [rbp-020h]
pop rbp
ret
sample ENDP
```

## <a name="see-also"></a>Voir aussi

[Assistances de déroulement pour MASM](../build/unwind-helpers-for-masm.md)