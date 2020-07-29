---
title: Erreur irrécupérable C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 110fbfe984ee7714e0c8ee2e2cb4deec4f43905a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207925"
---
# <a name="fatal-error-c1126"></a>Erreur irrécupérable C1126

'identificateur' : l’allocation automatique dépasse la taille

L’espace alloué pour les variables locales d’une fonction (plus une quantité limitée d’espace utilisé par le compilateur, comme des 20 octets supplémentaires pour les fonctions remplaçables) dépasse la limite.

Pour corriger cette erreur, utilisez `malloc` ou **`new`** pour allouer de grandes quantités de données.
