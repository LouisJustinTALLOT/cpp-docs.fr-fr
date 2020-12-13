---
description: En savoir plus sur :. PUSHREG
title: .PUSHREG
ms.date: 12/16/2019
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: b9316cebad76747c69cb577fcae71f28b6bd9530
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97131259"
---
# <a name="pushreg"></a>.PUSHREG

Génère une `UWOP_PUSH_NONVOL` entrée de code de déroulement pour le numéro de Registre spécifié à l’aide de l’offset actuel dans le prologue.

## <a name="syntax"></a>Syntaxe

> . *Registre* PUSHREG

## <a name="remarks"></a>Notes

**. PUSHREG** permet aux utilisateurs ml64.exe de spécifier le déroulement d’une fonction Frame et est uniquement autorisé dans le prologue, qui s’étend de la déclaration d' **image** [proc](proc.md) à la [. Directive ENDPROLOG](dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement `.xdata` et `.pdata` . **. Les PUSHREG** doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

le *Registre* peut être l’un des suivants : \
RAX | RCX | RDX | RBX | RDI | RSI | RBP | R8 | R9 | R10 | R11 | R12 | R13 | R14 | R15.

Pour plus d’informations, consultez [MASM pour x64 (ml64.exe)](masm-for-x64-ml64-exe.md).

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

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
