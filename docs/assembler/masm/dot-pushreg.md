---
title: .PUSHREG
ms.date: 08/30/2018
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: 2190bd05667de82dada34a63f11647c653f97247
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398033"
---
# <a name="pushreg"></a>.PUSHREG

Génère une entrée de code de déroulement `UWOP_PUSH_NONVOL` pour le numéro de Registre spécifié à l’aide de l’offset actuel dans le prologue.

## <a name="syntax"></a>Syntaxe

> . Registre PUSHREG

## <a name="remarks"></a>Notes

**. PUSHREG** permet aux utilisateurs de ml64. exe de spécifier le déroulement d’une fonction Frame et est uniquement autorisé dans le prologue, qui s’étend de la déclaration de la **trame** [proc](../../assembler/masm/proc.md) à l' [. Directive ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement des `.xdata` et des `.pdata`. **. Les PUSHREG** doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

Pour plus d’informations, consultez [MASM pour x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre comment envoyer des registres non volatils.

### <a name="code"></a>Code

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

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
