---
title: Erreur ML non fatale A2133
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: c2d13aefe02543129340bcc307771a1026776d61
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854613"
---
# <a name="ml-nonfatal-error-a2133"></a>Erreur ML non fatale A2133

**inscrire la valeur remplacée par INVOKE**

Un registre a été passé comme argument à une procédure, mais le code généré par [Invoke](../../assembler/masm/invoke.md) pour passer d’autres arguments a détruit le contenu du Registre.

Les registres AX, AL, AH, EAX, DX, DL, DH et EDX peuvent être utilisés par l’assembleur pour effectuer la conversion des données.

Utilisez un autre registre.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>