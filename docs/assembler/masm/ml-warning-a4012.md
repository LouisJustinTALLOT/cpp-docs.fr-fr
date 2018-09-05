---
title: Avertissement ML A4012 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A4012
dev_langs:
- C++
helpviewer_keywords:
- A4012
ms.assetid: 842b1259-9679-4eeb-a02d-672a583a94e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 083a0cd7687bc182aa9e387d6d575fa718b1b50c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682153"
---
# <a name="ml-warning-a4012"></a>Avertissement ML A4012

**informations de numéro de ligne pour le segment sans classe 'CODE'**

Portaient sur des instructions dans un segment qui n’avaient pas un nom de classe qui se termine par « CODE ». L’assembleur ne générait pas les informations CodeView pour ces instructions.

CodeView ne peut pas traiter des modules avec le code de segments avec des noms de classe qui ne se terminent pas par « CODE ».

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>