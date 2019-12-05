---
title: Erreur ML non fatale A2219
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: cf2be5db2aa9c21597c199a6840f4aaa50e0a681
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854587"
---
# <a name="ml-nonfatal-error-a2219"></a>Erreur ML non fatale A2219

> Alignement incorrect pour le décalage dans le code de déroulement

## <a name="remarks"></a>Notes

L’opérande pour [&period;ALLOCSTACK](../../assembler/masm/dot-allocstack.md) et [&period;SAVEREG](../../assembler/masm/dot-savereg.md) doit être un multiple de 8.  L’opérande pour [&period;SAVEXMM128](../../assembler/masm/dot-savexmm128.md) et [&period;SETFRAME](../../assembler/masm/dot-setframe.md) doit être un multiple de 16.

## <a name="see-also"></a>Voir aussi

[MILLILITREs de messages d’erreur](../../assembler/masm/ml-error-messages.md)
