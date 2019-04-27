---
title: .ALLOCSTACK
ms.date: 08/30/2018
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: b92db3d03bb5c45e67473cd4085f2369698f6b42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62185651"
---
# <a name="allocstack"></a>.ALLOCSTACK

Génère un **UWOP_ALLOC_SMALL** ou un **UWOP_ALLOC_LARGE** avec la taille spécifiée pour l’offset actuel dans le prologue.

## <a name="syntax"></a>Syntaxe

> . Taille ALLOCSTACK

## <a name="remarks"></a>Notes

MASM choisira l’encodage le plus efficace pour une taille donnée.

. ALLOCSTACK permet aux utilisateurs de ml64.exe spécifier la façon dont une fonction de frame se déroule et est autorisé uniquement dans le prologue, qui s’étend de la [PROC](../../assembler/masm/proc.md) déclaration FRAME pour le [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directive. Ces directives ne génèrent pas de code ; ils génèrent uniquement `.xdata` et `.pdata`. . ALLOCSTACK doit être précédé d’instructions qui implémentent les actions pour être déroulée. Il est conseillé pour encapsuler les directives de déroulement et le code qu’ils sont destinés à déroulement dans une macro pour garantir l’accord.

Le `size` opérande doit être un multiple de 8.

Pour plus d’informations, consultez la rubrique [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

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

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>