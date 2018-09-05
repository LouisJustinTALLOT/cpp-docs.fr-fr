---
title: ML erreur non fatale A2050 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd2e0e6c2fc818ef9286fd303c07a26bdd8b4e5a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680669"
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