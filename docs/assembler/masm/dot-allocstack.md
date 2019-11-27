---
title: .ALLOCSTACK
ms.date: 08/30/2018
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: 6d9d86371503992d1bebe738fb6e6773581b10e3
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398628"
---
# <a name="allocstack"></a>.ALLOCSTACK

Génère un **UWOP_ALLOC_SMALL** ou un **UWOP_ALLOC_LARGE** avec la taille spécifiée pour l’offset actuel dans le prologue.

## <a name="syntax"></a>Syntaxe

> **.**  *Taille* de ALLOCSTACK

## <a name="remarks"></a>Notes

MASM choisit l’encodage le plus efficace pour une taille donnée.

**. ALLOCSTACK** permet aux utilisateurs de ml64. exe de spécifier la façon dont une fonction frame est déroulée et qui est uniquement autorisée dans le prologue, qui s’étend de la déclaration de la trame [proc](../../assembler/masm/proc.md) à l' [. Directive ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement des `.xdata` et des `.pdata`. **. Les ALLOCSTACK** doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

L’opérande de *taille* doit être un multiple de 8.

Pour plus d’informations, consultez [MASM pour x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Exemple

L’exemple suivant montre comment spécifier un gestionnaire de déroulement/exception :

```asm
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console
text SEGMENT
PUBLIC Example3
PUBLIC Example3_UW
Example3_UW PROC NEAR
   ; exception/unwind handler body

   ret 0

Example3_UW ENDP

Example3 PROC FRAME : Example3_UW

   sub rsp, 16
.allocstack 16

.endprolog

   ; function body
    add rsp, 16
   ret 0

Example3 ENDP
text ENDS
END
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
