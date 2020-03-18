---
title: Utilisation de abort
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: e8cc7bce552acf67c0f9bf2025e0040dc051cff6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446426"
---
# <a name="using-abort"></a>Utilisation de abort

L’appel de la fonction [Abort](../c-runtime-library/reference/abort.md) provoque l’arrêt immédiat. Il ignore le processus normal de destruction des objets statiques globaux initialisés. Il ignore également tout traitement spécial qui a été spécifié avec la fonction `atexit`.

## <a name="see-also"></a>Voir aussi

[Considérations supplémentaires sur la terminaison](../cpp/additional-termination-considerations.md)