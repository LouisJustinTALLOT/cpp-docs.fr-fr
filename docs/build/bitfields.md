---
title: Champs de bits | Documents Microsoft
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
ms.openlocfilehash: 85db49f138cc733326e47a3008e79bae5ab4b7cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360778"
---
# <a name="bitfields"></a>Champs de bits
Structure les champs de bits sont limités à 64 bits et peut être de type signé int, int non signé, int64 ou unsigned int64. Les champs de bits qui dépassent la limite de type ignorent les bits pour aligner le champ de bits de l’alignement du type suivant. Par exemple, les champs de bits entier ne peuvent pas dépasser une limite de 32 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [Types et stockage](../build/types-and-storage.md)