---
title: ML erreur non fatale A2063 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2063
dev_langs:
- C++
helpviewer_keywords:
- A2063
ms.assetid: 12976b25-2159-4e0c-9df3-dcfac61091ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5ce02fcbab6452b45f38d7d8becff64a880d403
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680734"
---
# <a name="ml-nonfatal-error-a2063"></a>Erreur ML non fatale A2063

**peut aligner uniquement à la puissance de 2 : expression**

L’expression spécifiée avec le [ALIGN](../../assembler/masm/align-masm.md) directive n’était pas valide.

Le **ALIGN** expression doit être une puissance de 2 entre 2 et 256 et doit être inférieure ou égale à l’alignement du segment actuel, structure ou union.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>