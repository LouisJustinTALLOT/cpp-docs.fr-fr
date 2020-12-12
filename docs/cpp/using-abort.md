---
description: En savoir plus sur l’utilisation d’Abort
title: Utilisation de abort
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: 16c1df7a7b3a26be444d9b17d370366b1a41ea1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116858"
---
# <a name="using-abort"></a>Utilisation de abort

L’appel de la fonction [Abort](../c-runtime-library/reference/abort.md) provoque l’arrêt immédiat. Il ignore le processus normal de destruction des objets statiques globaux initialisés. Il ignore également tout traitement spécial qui a été spécifié avec la fonction `atexit`.

## <a name="see-also"></a>Voir aussi

[Autres considérations relatives à l’arrêt](../cpp/additional-termination-considerations.md)
