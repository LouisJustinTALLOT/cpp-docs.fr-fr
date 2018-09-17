---
title: Champs de bits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7451ea6afee81cc296fb091705bde48041ef5d1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722486"
---
# <a name="bitfields"></a>Champs de bits

Champs de bits de structure sont limités à 64 bits et peut être de type signé int, unsigned int, int64 ou unsigned int64. Les champs de bits qui dépassent la limite de type ignorent les bits pour aligner le champ de bits de l’alignement de type suivant. Par exemple, les champs de bits entier ne peuvent pas dépasser une limite de 32 bits.

## <a name="see-also"></a>Voir aussi

[Types et stockage](../build/types-and-storage.md)