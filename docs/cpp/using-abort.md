---
title: Utilisation de abort
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: db0f6cdcdaf4bca1b74d89a9415c4f7951455d80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187855"
---
# <a name="using-abort"></a>Utilisation de abort

L’appel de la fonction [Abort](../c-runtime-library/reference/abort.md) provoque l’arrêt immédiat. Il ignore le processus normal de destruction des objets statiques globaux initialisés. Il ignore également tout traitement spécial qui a été spécifié avec la fonction `atexit`.

## <a name="see-also"></a>Voir aussi

[Considérations supplémentaires sur la terminaison](../cpp/additional-termination-considerations.md)
