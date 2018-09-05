---
title: Erreur ML irrécupérable A1007 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1007
dev_langs:
- C++
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 539ab431510d5dc721e6531c11069a87e27c287a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693599"
---
# <a name="ml-fatal-error-a1007"></a>Erreur ML irrécupérable A1007

**niveau d’imbrication trop profond**

L’assembleur atteint sa limite d’imbrication. La limite est de 20 niveaux sauf indication contraire.

Parmi les options suivantes a été imbriqué trop profondément :

- Une directive de haut niveau tels que [. IF](../../assembler/masm/dot-if.md), [. RÉPÉTEZ](../../assembler/masm/dot-repeat.md), ou [. Bien que](../../assembler/masm/dot-while.md).

- Une définition de structure.

- Une directive conditionnelle de l’assembly.

- Une définition de procédure.

- Un [PUSHCONTEXT](../../assembler/masm/pushcontext.md) directive (la limite est 10).

- Une définition des segments.

- Un fichier include.

- Une macro.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>