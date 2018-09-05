---
title: ML erreur non fatale A2006 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f287c6ab46c6af71ba6dc0032f332ce3cc489454
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677403"
---
# <a name="ml-nonfatal-error-a2006"></a>Erreur ML non fatale A2006

**symbole non défini : identificateur**

Une tentative a tenté d’utiliser un symbole qui n’était pas défini.

Parmi les options suivantes peut-être se sont produites :

- Un symbole n’est pas défini.

- Un champ n’était pas un membre de la structure spécifiée.

- Un symbole a été défini dans un fichier include qui n’était pas inclus.

- Un symbole externe a été utilisé sans un [EXTERN](../../assembler/masm/extern-masm.md) ou [EXTERNDEF](../../assembler/masm/externdef.md) directive.

- Un nom de symbole a été mal orthographié.

- Une étiquette de code local a été référencée en dehors de son étendue.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>