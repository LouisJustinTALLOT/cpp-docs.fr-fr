---
description: 'En savoir plus sur : ML d’erreur non irrécupérable A2219'
title: Erreur ML non fatale A2219
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 3b9fd2f397f702a32784cd696bcbc3a72f35cf95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97128308"
---
# <a name="ml-nonfatal-error-a2219"></a>Erreur ML non fatale A2219

> Alignement incorrect pour le décalage dans le code de déroulement

## <a name="remarks"></a>Notes

L’opérande pour [ &period; ALLOCSTACK](dot-allocstack.md) et [ &period; SAVEREG](dot-savereg.md) doit être un multiple de 8.  L’opérande pour [ &period; SAVEXMM128](dot-savexmm128.md) et [ &period; SETFRAME](dot-setframe.md) doit être un multiple de 16.

## <a name="see-also"></a>Voir aussi

[MILLILITREs de messages d’erreur](ml-error-messages.md)
