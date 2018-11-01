---
title: .SETFRAME
ms.date: 08/30/2018
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: c2c35cdb2889350b27e9fb11c397b684506972c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506874"
---
# <a name="setframe"></a>.SETFRAME

Renseigne le frame inscrire champ et le décalage dans les informations de déroulement en utilisant le Registre spécifié (`reg`) et le décalage (`offset`). Le décalage doit être un multiple de 16 et inférieur ou égal à 240. Cette directive génère également un `UWOP_SET_FPREG` d’entrée du code de déroulement pour inscrire le texte spécifié à l’aide de l’offset de prologue actuel.

## <a name="syntax"></a>Syntaxe

> . SETFRAME reg, offset

## <a name="remarks"></a>Notes

. SETFRAME permet aux utilisateurs de ml64.exe spécifier comment se déroule une fonction de frame et est autorisée uniquement dans le prologue, qui s’étend de la [PROC](../../assembler/masm/proc.md) déclaration FRAME pour le [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directive. Ces directives ne génèrent pas de code ; ils génèrent uniquement `.xdata` et `.pdata`. . SETFRAME doit être précédé d’instructions qui implémentent les actions pour être déroulée. Il est conseillé pour encapsuler les directives de déroulement et le code qu’ils sont destinés à déroulement dans une macro pour garantir l’accord.

Pour plus d’informations, consultez [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre comment utiliser un pointeur de frame :

### <a name="code"></a>Code

```asm
; ml64 frmex2.asm /link /entry:frmex2 /SUBSYSTEM:CONSOLE
_text SEGMENT
frmex2 PROC FRAME
   push rbp
.pushreg rbp
   sub rsp, 010h
.allocstack 010h
   mov rbp, rsp
.setframe rbp, 0
.endprolog
   ; modify the stack pointer outside of the prologue (similar to alloca)
   sub rsp, 060h

   ; we can unwind from the following AV because of the frame pointer
   mov rax, 0
   mov rax, [rax] ; AV!

   add rsp, 060h
   add rsp, 010h
   pop rbp
   ret
frmex2 ENDP
_text ENDS
END
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>