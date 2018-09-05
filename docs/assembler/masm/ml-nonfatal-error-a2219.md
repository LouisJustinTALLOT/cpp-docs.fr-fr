---
title: ML erreur non fatale A2219 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2219
dev_langs:
- C++
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 365997181b0d4f4471162d7cf8f65a4429e69e74
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681643"
---
# <a name="ml-nonfatal-error-a2219"></a>Erreur ML non fatale A2219

**Code de déroulement de mauvais alignement pour le décalage dans**

L’opérande pour [. ALLOCSTACK](../../assembler/masm/dot-allocstack.md) et [. SAVEREG](../../assembler/masm/dot-savereg.md) doit être un multiple de 8.  L’opérande pour [. SAVEXMM128](../../assembler/masm/dot-savexmm128.md) et [. SETFRAME](../../assembler/masm/dot-setframe.md) doit être un multiple de 16.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>