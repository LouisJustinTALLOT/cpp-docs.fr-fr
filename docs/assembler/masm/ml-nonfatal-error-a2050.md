---
title: Erreur ML non fatale A2050
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 15c6449ff4207c92dee28120d4f61be641cf01c8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856575"
---
# <a name="ml-nonfatal-error-a2050"></a>Erreur ML non fatale A2050

**nombre réel ou BCD non autorisé**

Un nombre à virgule flottante (réel) ou une constante codée décimale binaire (BCD) a été utilisé autrement qu’en tant qu’initialiseur de données.

L’un des éléments suivants s’est produit :

- Un nombre réel ou un BCD a été utilisé dans une expression.

- Un nombre réel a été utilisé pour initialiser une directive autre que [DWORD](../../assembler/masm/dword.md), [QWord](../../assembler/masm/qword.md)ou [to](../../assembler/masm/tbyte.md).

- Un BCD a été utilisé pour initialiser une directive autre que `TBYTE`.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>