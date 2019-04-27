---
title: Erreur ML non fatale A2050
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 59d08b9c2743a3b45633527bcc54b3e1c4d6a58c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177550"
---
# <a name="ml-nonfatal-error-a2050"></a>Erreur ML non fatale A2050

**réel ou nombre de BCD ne pas autorisé**

Un nombre (réel) à virgule flottante ou une constante de binary coded decimal (BCD) a été utilisé autre que comme un initialiseur de données.

Parmi les options suivantes s’est produite :

- Un nombre réel ou un BCD a été utilisé dans une expression.

- Un nombre réel a été utilisé pour initialiser une directive autre que [DWORD](../../assembler/masm/dword.md), [QWORD](../../assembler/masm/qword.md), ou [to](../../assembler/masm/tbyte.md).

- Un BCD a été utilisé pour initialiser une directive autre que `TBYTE`.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>