---
title: Erreur ML non fatale A2006
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 058100984acbd42ac2993732ab619c0a27c0edd2
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317082"
---
# <a name="ml-nonfatal-error-a2006"></a>Erreur ML non fatale A2006

**symbole non défini : identificateur**

Une tentative a été faite pour utiliser un symbole qui n’a pas été défini.

L’une des conditions suivantes peut se produire :

- Aucun symbole n’a été défini.

- Un champ n’était pas un membre de la structure spécifiée.

- Un symbole a été défini dans un fichier include qui n’a pas été inclus.

- Un symbole externe a été utilisé sans directive [extern](extern-masm.md) ou [EXTERNDEF](externdef.md) .

- Un nom de symbole a été mal orthographié.

- Une étiquette de code local a été référencée en dehors de son étendue.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](ml-error-messages.md)
