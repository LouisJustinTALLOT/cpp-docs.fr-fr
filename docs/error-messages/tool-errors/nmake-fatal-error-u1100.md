---
title: Erreur irrécupérable NMAKE U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: d5c62c1465bbb6463afbac2bc9ad5f4290473471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193262"
---
# <a name="nmake-fatal-error-u1100"></a>Erreur irrécupérable NMAKE U1100

la macro « nommacro » n’est pas conforme dans le contexte de la règle de lot « règle »

NMAKE génère cette erreur lorsque le bloc de commandes d’une règle en mode batch fait directement ou indirectement référence à une macro de fichier spéciale qui n’est pas $ <.

$ < est la seule macro autorisée pour les règles en mode batch.
