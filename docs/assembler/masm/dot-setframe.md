---
title: .SETFRAME
ms.date: 08/30/2018
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: a21dda496d32abcfeb4692d0228afdbcfd4e5ebb
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397928"
---
# <a name="setframe"></a>.SETFRAME

Remplit le champ du Registre du frame et le décalage dans les informations de déroulement à l’aide du Registre (*reg*) et du décalage (*offset*) spécifiés. Le décalage doit être un multiple de 16 et inférieur ou égal à 240. Cette directive génère également une entrée de code de déroulement `UWOP_SET_FPREG` pour le registre spécifié à l’aide de l’offset de prologue actuel.

## <a name="syntax"></a>Syntaxe

> **. SETFRAME** *reg*, *décalage*

## <a name="remarks"></a>Notes

**. SETFRAME** permet aux utilisateurs de ml64. exe de spécifier le déroulement d’une fonction Frame et est uniquement autorisé dans le prologue, qui s’étend de la déclaration de la trame [proc](../../assembler/masm/proc.md) à l' [. Directive ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement des `.xdata` et des `.pdata`. **. Les SETFRAME** doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

Pour plus d’informations, consultez [MASM pour x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

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

[Informations de référence sur les directives](directives-reference.md)
