---
title: Erreur ML non fatale A2219
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 611be49a1d4018eeb4edd9ee750d5a0614a83abe
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75311947"
---
# <a name="ml-nonfatal-error-a2219"></a>Erreur ML non fatale A2219

> Alignement incorrect pour le décalage dans le code de déroulement

## <a name="remarks"></a>Notes

L’opérande pour [&period;ALLOCSTACK](dot-allocstack.md) et [&period;SAVEREG](dot-savereg.md) doit être un multiple de 8.  L’opérande pour [&period;SAVEXMM128](dot-savexmm128.md) et [&period;SETFRAME](dot-setframe.md) doit être un multiple de 16.

## <a name="see-also"></a>Voir aussi

[MILLILITREs de messages d’erreur](ml-error-messages.md)
