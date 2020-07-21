---
title: Erreur irrécupérable NMAKE U1100
description: Description des causes de l’erreur irrécupérable Microsoft NMAKE NMAKE U1100.
ms.date: 07/17/2020
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: f908514469a6c9fdb53df3b2bded1b30bddc5a41
ms.sourcegitcommit: 00af3df3331854b23693ee844e5e7c10c8b05a90
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86491386"
---
# <a name="nmake-fatal-error-u1100"></a>Erreur irrécupérable NMAKE U1100

> la macro «*macro-Name*» n’est pas conforme dans le contexte de la règle batch «*rule-name*»

NMAKE génère cette erreur lorsque le bloc de commandes d’une règle en mode batch fait directement ou indirectement référence à une macro de fichier spéciale qui n’est pas `$<` .

`$<`est la seule macro autorisée pour les règles en mode batch.

Pour plus d’informations sur les macros NMAKE dans les règles de traitement par lots, consultez [macros NMAKE spéciales](../../build/reference/special-nmake-macros.md).
