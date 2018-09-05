---
title: Erreur ML irrécupérable A1009 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1009
dev_langs:
- C++
helpviewer_keywords:
- A1009
ms.assetid: f7a962a6-4280-485e-95cb-2ab8922c66c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5dde8fbc68fa125afd71798707acad879691af23
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687082"
---
# <a name="ml-fatal-error-a1009"></a>Erreur ML irrécupérable A1009

**ligne trop longue**

Une ligne dans un fichier source a dépassé la limite de 512 caractères.

Si plusieurs lignes physiques sont concaténés avec le caractère de continuation de ligne (\), la ligne logique qui en résulte est toujours limitée à 512 caractères.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>