---
title: Macros MASM
ms.date: 11/04/2016
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
ms.openlocfilehash: 8a00852a3a763aae5fda34d7e0fde664997a0bdb
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328823"
---
# <a name="masm-macros"></a>Macros MASM

Afin de simplifier l’utilisation de la [pseudo-opérations brutes](../build/raw-pseudo-operations.md), il existe un ensemble de macros, défini dans ksamd64.inc, qui peut être utilisé pour créer des prologues et épilogues.

## <a name="remarks"></a>Notes

|Macro|Description|
|-----------|-----------------|
|alloc_stack(n)|Alloue un frame de pile de n octets (à l’aide de sub rsp, n) et émet des informations (.allocstack n) de déroulement appropriées|
|save_reg reg, loc|Enregistre un reg Registre non volatil sur la pile à l’emplacement de l’offset RSP et émet des informations de déroulement appropriées. (.savereg reg, loc)|
|push_reg reg|Exécute un push d’un Registre de Registre non volatil sur la pile et émet des informations de déroulement appropriées. (.pushreg reg)|
|rex_push_reg reg|Enregistrer un Registre non volatil sur la pile à l’aide d’un push de 2 octets et émet des informations (.pushreg reg) doit être utilisée que si la notification push est la première instruction dans la fonction pour vous assurer que la fonction est corrigeable en chaud-mémoire de déroulement appropriées.|
|save_xmm128 reg, loc|Enregistre un registre XMM non volatil reg sur la pile à l’emplacement de l’offset RSP et émet des informations (.savexmm128 reg, loc) de déroulement appropriées|
|set_frame reg, offset|Définit le reg register frame pour le RSP + décalage (à l’aide de mov ou un laisser) et émet des informations (.set_frame reg, offset) de déroulement appropriées|
|push_eflags|Exécute un push des eflags avec une instruction pushfq et émet des informations (.alloc_stack 8) de déroulement appropriées|

Voici un exemple de prologue de fonction avec une utilisation correcte des macros :

```asm
SkFrame struct
Fill    dq ?; fill to 8 mod 16
SavedRdi dq ?; saved register RDI
SavedRsi dq ?; saved register RSI
SkFrame ends

sampleFrame struct
Filldq?; fill to 8 mod 16
SavedRdidq?; Saved Register RDI
SavedRsi  dq?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
alloc_stack(sizeof sampleFrame)
save_reg rdi, sampleFrame.SavedRdi
save_reg rsi, sampleFrame.SavedRsi
.end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here’s the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="see-also"></a>Voir aussi

[Assistances de déroulement pour MASM](../build/unwind-helpers-for-masm.md)