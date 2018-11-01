---
title: Erreur des outils Éditeur de liens LNK1120
ms.date: 05/17/2017
f1_keywords:
- LNK1120
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
ms.openlocfilehash: b11318dcffb665d3b422fffcbd7e6275f35984dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490803"
---
# <a name="linker-tools-error-lnk1120"></a>Erreur des outils Éditeur de liens LNK1120

> *nombre* externes non résolus

L’erreur LNK1120 signale le nombre (*nombre*) des erreurs de symbole externe non résolu pour cette opération de liaison. La plupart non résolu les erreurs de symbole externe sont signalées individuellement par [erreur des outils Éditeur de liens LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md) et [erreur des outils Éditeur de liens LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md), qui précèdent ce message d’erreur, une fois pour chaque symbole externe non résolu Erreur de symbole.

Pour corriger cette erreur, corrigez toutes les autres erreurs externes non résolues ou d’autres erreurs de l’éditeur de liens qui la précèdent dans la sortie de génération. Cette erreur n’est pas signalée lorsqu’il ne reste aucune erreur externe non résolu.
