---
title: Erreur ML non fatale A2096
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: 14fb30214cf7badf51368672dc52635d50a067f1
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855472"
---
# <a name="ml-nonfatal-error-a2096"></a>Erreur ML non fatale A2096

**Registre de segment, de groupe ou de segment ATTENDU**

Un segment ou un groupe était attendu mais n’a pas été trouvé.

L’un des éléments suivants s’est produit :

- L’opérande gauche spécifié avec l’opérateur de substitution de segment ( **:** ) n’est pas un registre de segment (CS, DS, SS, ES, FS ou GS), un nom de groupe, un nom de segment ou une expression de segment.

- La directive [supposer](../../assembler/masm/assume.md) a reçu un registre de segment sans adresse de segment valide, registre de segment, groupe ou groupe **plat** spécial.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>