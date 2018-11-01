---
title: Utilisation de abort
ms.date: 11/04/2016
f1_keywords:
- Abort
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: 0961f6f88f5de4d435fa65e50b9dbdbc478e7608
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591826"
---
# <a name="using-abort"></a>Utilisation de abort

Appel de la [abandonner](../c-runtime-library/reference/abort.md) fonction provoque l’arrêt immédiat. Il ignore le processus normal de destruction des objets statiques globaux initialisés. Il ignore également tout traitement spécial qui a été spécifié avec la fonction `atexit`.

## <a name="see-also"></a>Voir aussi

[Considérations supplémentaires sur la terminaison](../cpp/additional-termination-considerations.md)