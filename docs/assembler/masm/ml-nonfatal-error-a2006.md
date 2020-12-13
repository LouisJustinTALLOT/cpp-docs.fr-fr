---
description: 'En savoir plus sur : ML d’erreur non irrécupérable A2006'
title: Erreur ML non fatale A2006
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: c9057b600d9f9ed11f31009c3964aac028ffa1f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129413"
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

[Messages d'erreur ML](ml-error-messages.md)
