---
title: Erreur ML irrécupérable A1007
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 01633b4fa084b7d5e14af5a5c6e51e3dca684d2a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856915"
---
# <a name="ml-fatal-error-a1007"></a>Erreur ML irrécupérable A1007

**niveau d’imbrication trop profond**

L’assembleur a atteint sa limite d’imbrication. La limite est de 20 niveaux sauf mention contraire.

L’un des éléments suivants a été imbriqué trop profondément :

- Directive de niveau supérieur, telle que [. Si](../../assembler/masm/dot-if.md), [. REPEAT](../../assembler/masm/dot-repeat.md), ou [. WHILe](../../assembler/masm/dot-while.md).

- Définition de structure.

- Directive d’assembly conditionnel.

- Définition de procédure.

- Directive [PUSHCONTEXT](../../assembler/masm/pushcontext.md) (la limite est 10).

- Définition de segment.

- Fichier include.

- Une macro.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>