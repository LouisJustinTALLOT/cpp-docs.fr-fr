---
title: Utilisation d’abort | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3edc24b2b8dc869022039d4aaaea73af06eac16b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092527"
---
# <a name="using-abort"></a>Utilisation de abort

Appel de la [abandonner](../c-runtime-library/reference/abort.md) fonction provoque l’arrêt immédiat. Il ignore le processus normal de destruction des objets statiques globaux initialisés. Il ignore également tout traitement spécial qui a été spécifié avec la fonction `atexit`.

## <a name="see-also"></a>Voir aussi

[Considérations supplémentaires sur la terminaison](../cpp/additional-termination-considerations.md)