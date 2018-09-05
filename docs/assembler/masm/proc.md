---
title: PROC | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- PROC
dev_langs:
- C++
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ee26e181f0f40126c86a36889c43405f0b40f5e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680844"
---
# <a name="proc"></a>PROC

Marque le début et fin d’un bloc de procédure appelé *étiquette*. Les instructions dans le bloc peuvent être appelées avec le **appeler** instruction ou [INVOKE](../../assembler/masm/invoke.md) directive.

## <a name="syntax"></a>Syntaxe

> *étiquette* PROC [[*distance*]] [[*langtype*]] [[*visibilité*]] [[\<*prologuearg*>]] [[ UTILISE *reglist*]] [[, *paramètre* [[ :*balise*]]]...<br/>
> [[FRAME [[ :*ehandler-adresse*]]]]<br/>
> *Instructions*<br/>
> *étiquette* ENDP

## <a name="remarks"></a>Notes

[[FRAME [[ :*ehandler-adresse*]]]] est uniquement valide avec ml64.exe et génère MASM générer une entrée de table de fonction dans .pdata et .xdata d’informations de déroulement pour une fonction de structuré comportement de déroulement de la gestion des exceptions.

Lorsque le **FRAME** attribut est utilisé, il doit être suivi par un [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directive.

Consultez [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) pour plus d’informations sur l’utilisation de ml64.exe.

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

Le code ci-dessus émettre le tableau suivant de la fonction et informations de déroulement :

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

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>