---
title: Erreur irrécupérable NMAKE U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: a1474acab4ca4929fb4db4b7b78d7a96637a0745
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666594"
---
# <a name="nmake-fatal-error-u1100"></a>Erreur irrécupérable NMAKE U1100

la macro 'nom_macro' non conforme dans le contexte de la règle batch 'règle'

NMAKE génère cette erreur lorsque le bloc de commandes d’une règle en mode batch directement ou indirectement référence à une macro de fichier spécial qui n’est pas $<.

$< est le seul autorisé macro pour les règles en mode batch.