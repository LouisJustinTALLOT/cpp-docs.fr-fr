---
title: Erreur ML irrécupérable A1007
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: c9527769e0d9397de90f49cbce98b2cca42bed50
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317121"
---
# <a name="ml-fatal-error-a1007"></a>Erreur ML irrécupérable A1007

**niveau d’imbrication trop profond**

L’assembleur a atteint sa limite d’imbrication. La limite est de 20 niveaux sauf mention contraire.

L’un des éléments suivants a été imbriqué trop profondément :

- Directive de niveau supérieur, telle que [. Si](dot-if.md), [. REPEAT](dot-repeat.md), ou [. WHILe](dot-while.md).

- Définition de structure.

- Directive d’assembly conditionnel.

- Définition de procédure.

- Directive [PUSHCONTEXT](pushcontext.md) (la limite est 10).

- Définition de segment.

- Fichier include.

- Une macro.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](ml-error-messages.md)
