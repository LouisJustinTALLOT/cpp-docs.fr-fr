---
title: Erreur ML non fatale A2050
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 311aedd0cc739fd862efb0a18cc444b3fb75b165
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316978"
---
# <a name="ml-nonfatal-error-a2050"></a>Erreur ML non fatale A2050

**nombre réel ou BCD non autorisé**

Un nombre à virgule flottante (réel) ou une constante codée décimale binaire (BCD) a été utilisé autrement qu’en tant qu’initialiseur de données.

L’un des éléments suivants s’est produit :

- Un nombre réel ou un BCD a été utilisé dans une expression.

- Un nombre réel a été utilisé pour initialiser une directive autre que [DWORD](dword.md), [QWord](qword.md)ou [to](tbyte.md).

- Un BCD a été utilisé pour initialiser une directive autre que `TBYTE`.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](ml-error-messages.md)
